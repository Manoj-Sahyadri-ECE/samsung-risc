#include "ch32v00x.h"
#define IR_Left_Pin    GPIO_Pin_0
#define IR_Middle_Pin  GPIO_Pin_1
#define IR_Right_Pin   GPIO_Pin_2

#define Motor_Left_Fwd_Pin  GPIO_Pin_3
#define Motor_Left_Bwd_Pin  GPIO_Pin_4
#define Motor_Right_Fwd_Pin GPIO_Pin_5
#define Motor_Right_Bwd_Pin GPIO_Pin_6

void GPIO_Config(void) {
    RCC_APB2PeriphClockCmd(RCC_APB2Periph_GPIOA, ENABLE);
    GPIO_InitTypeDef GPIO_InitStructure;
    GPIO_InitStructure.GPIO_Pin = IR_Left_Pin | IR_Middle_Pin | IR_Right_Pin;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_IPU;  
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOA, &GPIO_InitStructure);

    // Configure motor control pins as output
    GPIO_InitStructure.GPIO_Pin = Motor_Left_Fwd_Pin | Motor_Left_Bwd_Pin | Motor_Right_Fwd_Pin | Motor_Right_Bwd_Pin;
    GPIO_InitStructure.GPIO_Mode = GPIO_Mode_Out_PP; 
    GPIO_InitStructure.GPIO_Speed = GPIO_Speed_50MHz;
    GPIO_Init(GPIOA, &GPIO_InitStructure);
}

void Motor_Forward(void) {
    GPIO_SetBits(GPIOA, Motor_Left_Fwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Left_Bwd_Pin);
    GPIO_SetBits(GPIOA, Motor_Right_Fwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Right_Bwd_Pin);
}

void Motor_Backward(void) {
    GPIO_ResetBits(GPIOA, Motor_Left_Fwd_Pin);
    GPIO_SetBits(GPIOA, Motor_Left_Bwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Right_Fwd_Pin);
    GPIO_SetBits(GPIOA, Motor_Right_Bwd_Pin);
}

void Motor_Stop(void) {
    GPIO_ResetBits(GPIOA, Motor_Left_Fwd_Pin | Motor_Left_Bwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Right_Fwd_Pin | Motor_Right_Bwd_Pin);
}

void Motor_Turn_Left(void) {
    GPIO_ResetBits(GPIOA, Motor_Left_Fwd_Pin | Motor_Left_Bwd_Pin);
    GPIO_SetBits(GPIOA, Motor_Right_Fwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Right_Bwd_Pin);
}

void Motor_Turn_Right(void) {
    GPIO_SetBits(GPIOA, Motor_Left_Fwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Left_Bwd_Pin);
    GPIO_ResetBits(GPIOA, Motor_Right_Fwd_Pin | Motor_Right_Bwd_Pin);
}

int Read_IR_Sensors(void) {
    int left = GPIO_ReadInputDataBit(GPIOA, IR_Left_Pin);
    int middle = GPIO_ReadInputDataBit(GPIOA, IR_Middle_Pin);
    int right = GPIO_ReadInputDataBit(GPIOA, IR_Right_Pin);

    return (left << 2) | (middle << 1) | right; 
}

void Line_Follower(void) {
    int sensor_status = Read_IR_Sensors();
    switch (sensor_status) {
        case 0b111:  
            Motor_Forward();
            break;
        case 0b011:  
            Motor_Turn_Right();
            break;
        case 0b101:  
            Motor_Turn_Left();
            break;
        case 0b001:  
            Motor_Forward();
            break;
        case 0b110: 
            Motor_Forward();
            break;
        case 0b010:  
            Motor_Forward();
            break;
        case 0b000:  
            Motor_Stop();
            break;
        default:  
            Motor_Stop();
            break;
    }
}

int main(void) {
    SystemInit();
    GPIO_Config();

    while(1) {
        Line_Follower();
    }
}

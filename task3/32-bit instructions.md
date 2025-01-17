# 1. MULH A0, A1, A2
| funct7  | rs2  | rs1  | funct3 | rd   | opcode  |
|---------|------|------|--------|------|---------|
| 0000001 | a2   | a1   | 001    | a0   | 0110011 |

# 2. FADD.S F0, F1, F2
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 0         | F1   | 000    | F0   | 1010011 |

# 3. FSUB.S F0, F1, F2
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 0         | F1   | 001    | F0   | 1010011 |

# 4. FMUL.S F0, F1, F2
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 0         | F1   | 010    | F0   | 1010011 |

# 5. FDIV.S F0, F1, F2
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 0         | F1   | 011    | F0   | 1010011 |

# 6. FLW F0, 0(SP)
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 0         | sp   | 010    | F0   | 0000011 |

# 7. FSW F0, 0(SP)
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 0         | sp   | 010    | F0   | 0100011 |

# 8. BEQZ A0, -8
| imm[12] | imm[10:5] | rs2  | rs1  | funct3 | imm[4:1] | imm[11] | opcode  |
|---------|-----------|------|------|--------|----------|---------|---------|
| 1       | 111111    | zero | a0   | 000    | 0110     | 1       | 1100011 |

# 9. BGEZ A0, 10
| imm[12] | imm[10:5] | rs2  | rs1  | funct3 | imm[4:1] | imm[11] | opcode  |
|---------|-----------|------|------|--------|----------|---------|---------|
| 0       | 000000    | zero | a0   | 101    | 0101     | 1       | 1100011 |

# 10. BGE A0, A1, 15
| imm[12] | imm[10:5] | rs2  | rs1  | funct3 | imm[4:1] | imm[11] | opcode  |
|---------|-----------|------|------|--------|----------|---------|---------|
| 1       | 000001    | a1   | a0   | 101    | 0111     | 0       | 1100011 |

# 11. SLTIU A0, A1, 32
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 32        | a1   | 011    | a0   | 0010011 |

# 12. LBU A0, 8(SP)
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 8         | sp   | 100    | a0   | 0000011 |

# 13. SLTI A0, A1, 50
| imm[11:0] | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 50        | a1   | 010    | a0   | 0010011 |

# 14. SRLI A0, A1, 4
| imm[5:0]  | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 000100    | a1   | 101    | a0   | 0010011 |

# 15. SLLI A0, A1, 3
| imm[5:0]  | rs1  | funct3 | rd   | opcode  |
|-----------|------|--------|------|---------|
| 000011    | a1   | 001    | a0   | 0010011 |
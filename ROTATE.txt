       LD E,02H
       IN A,(00H)
       LD B,A
       AND 01H
       LD D,A
       LD A,B
       CALL DIV
       LD A,00H
       ADD A,D
       JP NZ,ONER
       LD A,C
CONR   CALL BCDR
       LD E,02H
       IN A,(10H)
       LD B,A
       AND 80H
       LD D,A
       LD A,B
       ADD A,A
       LD B,A
       LD A,00H
       ADD A,D
       JP NZ,ONEL
       LD A,B
CONL   CALL BCDL
       HALT
ONER   LD A,C
       OR 80H
       JP CONR
ONEL   LD A,B
       OR 01H
       JP CONL
DIV    LD C,00H
LOOP   INC C
       SUB E
       JP C,MIN
       JP NZ,LOOP
END    RET
MIN    DEC C
       ADD A,E
       JP END
BCDR   LD E,0AH
       CALL DIV
       OUT (05H),A
       LD A,C
       CALL DIV
       OUT (04H),A
       LD A,C
       OUT (03H),A
       RET
BCDL   LD E,0AH
       CALL DIV
       OUT (15H),A
       LD A,C
       CALL DIV
       OUT (14H),A
       LD A,C
       OUT (13H),A
       RET
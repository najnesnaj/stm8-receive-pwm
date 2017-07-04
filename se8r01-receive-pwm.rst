                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul 11 2014) (Linux)
                                      4 ; This file was generated Tue Jul  4 11:51:56 2017
                                      5 ;--------------------------------------------------------
                                      6 	.module se8r01_receive_pwm
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _main
                                     13 	.globl _SE8R01_Init
                                     14 	.globl _SE8R01_Analog_Init
                                     15 	.globl _SE8R01_Calibration
                                     16 	.globl _rf_switch_bank
                                     17 	.globl _init_io
                                     18 	.globl _InitializeUART
                                     19 	.globl _print_UCHAR_hex
                                     20 	.globl _UARTPrintF
                                     21 	.globl _delay
                                     22 	.globl _InitializeSystemClock
                                     23 	.globl _InitializeSPI
                                     24 	.globl _read_spi_buf
                                     25 	.globl _write_spi_buf
                                     26 	.globl _read_spi_reg
                                     27 	.globl _write_spi_reg
                                     28 	.globl _write_spi
                                     29 	.globl _delayTenMicro
                                     30 	.globl _memset
                                     31 	.globl _tx_buf
                                     32 	.globl _rx_buf
                                     33 	.globl _ADDRESS0
                                     34 	.globl _ADDRESS1
                                     35 	.globl _ADDRESS5
                                     36 	.globl _ADDRESS4
                                     37 	.globl _ADDRESS3
                                     38 	.globl _ADDRESS2
                                     39 	.globl _TX_ADDRESS
                                     40 	.globl _status
                                     41 	.globl _pip
                                     42 	.globl _signal_lv
                                     43 	.globl _newdata
                                     44 	.globl _pload_width_now
                                     45 	.globl _SE8R01_DR_500K
                                     46 	.globl _SE8R01_DR_1M
                                     47 	.globl _SE8R01_DR_2M
                                     48 	.globl _myData_pip4
                                     49 	.globl _myData_pip5
                                     50 	.globl _gtemp
                                     51 ;--------------------------------------------------------
                                     52 ; ram data
                                     53 ;--------------------------------------------------------
                                     54 	.area DATA
      000001                         55 _gtemp::
      000001                         56 	.ds 5
      000006                         57 _myData_pip5::
      000006                         58 	.ds 5
      00000B                         59 _myData_pip4::
      00000B                         60 	.ds 5
                                     61 ;--------------------------------------------------------
                                     62 ; ram data
                                     63 ;--------------------------------------------------------
                                     64 	.area INITIALIZED
      000010                         65 _SE8R01_DR_2M::
      000010                         66 	.ds 2
      000012                         67 _SE8R01_DR_1M::
      000012                         68 	.ds 2
      000014                         69 _SE8R01_DR_500K::
      000014                         70 	.ds 2
      000016                         71 _pload_width_now::
      000016                         72 	.ds 2
      000018                         73 _newdata::
      000018                         74 	.ds 2
      00001A                         75 _signal_lv::
      00001A                         76 	.ds 1
      00001B                         77 _pip::
      00001B                         78 	.ds 2
      00001D                         79 _status::
      00001D                         80 	.ds 1
      00001E                         81 _TX_ADDRESS::
      00001E                         82 	.ds 4
      000022                         83 _ADDRESS2::
      000022                         84 	.ds 1
      000023                         85 _ADDRESS3::
      000023                         86 	.ds 1
      000024                         87 _ADDRESS4::
      000024                         88 	.ds 1
      000025                         89 _ADDRESS5::
      000025                         90 	.ds 1
      000026                         91 _ADDRESS1::
      000026                         92 	.ds 4
      00002A                         93 _ADDRESS0::
      00002A                         94 	.ds 4
      00002E                         95 _rx_buf::
      00002E                         96 	.ds 32
      00004E                         97 _tx_buf::
      00004E                         98 	.ds 32
                                     99 ;--------------------------------------------------------
                                    100 ; Stack segment in internal ram 
                                    101 ;--------------------------------------------------------
                                    102 	.area	SSEG
      000000                        103 __start__stack:
      000000                        104 	.ds	1
                                    105 
                                    106 ;--------------------------------------------------------
                                    107 ; absolute external ram data
                                    108 ;--------------------------------------------------------
                                    109 	.area DABS (ABS)
                                    110 ;--------------------------------------------------------
                                    111 ; interrupt vector 
                                    112 ;--------------------------------------------------------
                                    113 	.area HOME
      008000                        114 __interrupt_vect:
      008000 82 00 80 83            115 	int s_GSINIT ;reset
      008004 82 00 00 00            116 	int 0x0000 ;trap
      008008 82 00 00 00            117 	int 0x0000 ;int0
      00800C 82 00 00 00            118 	int 0x0000 ;int1
      008010 82 00 00 00            119 	int 0x0000 ;int2
      008014 82 00 00 00            120 	int 0x0000 ;int3
      008018 82 00 00 00            121 	int 0x0000 ;int4
      00801C 82 00 00 00            122 	int 0x0000 ;int5
      008020 82 00 00 00            123 	int 0x0000 ;int6
      008024 82 00 00 00            124 	int 0x0000 ;int7
      008028 82 00 00 00            125 	int 0x0000 ;int8
      00802C 82 00 00 00            126 	int 0x0000 ;int9
      008030 82 00 00 00            127 	int 0x0000 ;int10
      008034 82 00 00 00            128 	int 0x0000 ;int11
      008038 82 00 00 00            129 	int 0x0000 ;int12
      00803C 82 00 00 00            130 	int 0x0000 ;int13
      008040 82 00 00 00            131 	int 0x0000 ;int14
      008044 82 00 00 00            132 	int 0x0000 ;int15
      008048 82 00 00 00            133 	int 0x0000 ;int16
      00804C 82 00 00 00            134 	int 0x0000 ;int17
      008050 82 00 00 00            135 	int 0x0000 ;int18
      008054 82 00 00 00            136 	int 0x0000 ;int19
      008058 82 00 00 00            137 	int 0x0000 ;int20
      00805C 82 00 00 00            138 	int 0x0000 ;int21
      008060 82 00 00 00            139 	int 0x0000 ;int22
      008064 82 00 00 00            140 	int 0x0000 ;int23
      008068 82 00 00 00            141 	int 0x0000 ;int24
      00806C 82 00 00 00            142 	int 0x0000 ;int25
      008070 82 00 00 00            143 	int 0x0000 ;int26
      008074 82 00 00 00            144 	int 0x0000 ;int27
      008078 82 00 00 00            145 	int 0x0000 ;int28
      00807C 82 00 00 00            146 	int 0x0000 ;int29
                                    147 ;--------------------------------------------------------
                                    148 ; global & static initialisations
                                    149 ;--------------------------------------------------------
                                    150 	.area HOME
                                    151 	.area GSINIT
                                    152 	.area GSFINAL
                                    153 	.area GSINIT
      008083                        154 __sdcc_gs_init_startup:
      008083                        155 __sdcc_init_data:
                                    156 ; stm8_genXINIT() start
      008083 AE 00 0F         [ 2]  157 	ldw x, #l_DATA
      008086 27 07            [ 1]  158 	jreq	00002$
      008088                        159 00001$:
      008088 72 4F 00 00      [ 1]  160 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  161 	decw x
      00808D 26 F9            [ 1]  162 	jrne	00001$
      00808F                        163 00002$:
      00808F AE 00 5E         [ 2]  164 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  165 	jreq	00004$
      008094                        166 00003$:
      008094 D6 89 B7         [ 1]  167 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 0F         [ 1]  168 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  169 	decw	x
      00809B 26 F7            [ 1]  170 	jrne	00003$
      00809D                        171 00004$:
                                    172 ; stm8_genXINIT() end
                                    173 	.area GSFINAL
      00809D CC 80 80         [ 2]  174 	jp	__sdcc_program_startup
                                    175 ;--------------------------------------------------------
                                    176 ; Home
                                    177 ;--------------------------------------------------------
                                    178 	.area HOME
                                    179 	.area HOME
      008080                        180 __sdcc_program_startup:
      008080 CC 87 C4         [ 2]  181 	jp	_main
                                    182 ;	return from main will return to caller
                                    183 ;--------------------------------------------------------
                                    184 ; code
                                    185 ;--------------------------------------------------------
                                    186 	.area CODE
                                    187 ;	se8r01-receive-pwm.c: 46: void delayTenMicro (void) {
                                    188 ;	-----------------------------------------
                                    189 ;	 function delayTenMicro
                                    190 ;	-----------------------------------------
      0080A0                        191 _delayTenMicro:
                                    192 ;	se8r01-receive-pwm.c: 48: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  193 	ld	a, #0x32
      0080A2                        194 00104$:
                                    195 ;	se8r01-receive-pwm.c: 49: __asm__("nop");
      0080A2 9D               [ 1]  196 	nop
      0080A3 4A               [ 1]  197 	dec	a
                                    198 ;	se8r01-receive-pwm.c: 48: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  199 	tnz	a
      0080A5 26 FB            [ 1]  200 	jrne	00104$
      0080A7 81               [ 4]  201 	ret
                                    202 ;	se8r01-receive-pwm.c: 51: UCHAR write_spi (UCHAR value) {
                                    203 ;	-----------------------------------------
                                    204 ;	 function write_spi
                                    205 ;	-----------------------------------------
      0080A8                        206 _write_spi:
                                    207 ;	se8r01-receive-pwm.c: 53: delayTenMicro ();
      0080A8 CD 80 A0         [ 4]  208 	call	_delayTenMicro
                                    209 ;	se8r01-receive-pwm.c: 54: SPI_DR = value;
      0080AB AE 52 04         [ 2]  210 	ldw	x, #0x5204
      0080AE 7B 03            [ 1]  211 	ld	a, (0x03, sp)
      0080B0 F7               [ 1]  212 	ld	(x), a
                                    213 ;	se8r01-receive-pwm.c: 55: delayTenMicro ();
      0080B1 CD 80 A0         [ 4]  214 	call	_delayTenMicro
                                    215 ;	se8r01-receive-pwm.c: 56: while ((SPI_SR & TXE) == 0);
      0080B4                        216 00101$:
      0080B4 AE 52 03         [ 2]  217 	ldw	x, #0x5203
      0080B7 F6               [ 1]  218 	ld	a, (x)
      0080B8 A5 02            [ 1]  219 	bcp	a, #0x02
      0080BA 27 F8            [ 1]  220 	jreq	00101$
                                    221 ;	se8r01-receive-pwm.c: 57: delayTenMicro ();
      0080BC CD 80 A0         [ 4]  222 	call	_delayTenMicro
                                    223 ;	se8r01-receive-pwm.c: 58: while ((SPI_SR & RXNE) == 0);
      0080BF                        224 00104$:
      0080BF AE 52 03         [ 2]  225 	ldw	x, #0x5203
      0080C2 F6               [ 1]  226 	ld	a, (x)
      0080C3 44               [ 1]  227 	srl	a
      0080C4 24 F9            [ 1]  228 	jrnc	00104$
                                    229 ;	se8r01-receive-pwm.c: 59: delayTenMicro ();
      0080C6 CD 80 A0         [ 4]  230 	call	_delayTenMicro
                                    231 ;	se8r01-receive-pwm.c: 60: ret = SPI_DR;
      0080C9 AE 52 04         [ 2]  232 	ldw	x, #0x5204
      0080CC F6               [ 1]  233 	ld	a, (x)
                                    234 ;	se8r01-receive-pwm.c: 61: return (ret);
      0080CD 81               [ 4]  235 	ret
                                    236 ;	se8r01-receive-pwm.c: 63: UCHAR write_spi_reg (UCHAR reg, UCHAR value) {
                                    237 ;	-----------------------------------------
                                    238 ;	 function write_spi_reg
                                    239 ;	-----------------------------------------
      0080CE                        240 _write_spi_reg:
      0080CE 88               [ 1]  241 	push	a
                                    242 ;	se8r01-receive-pwm.c: 65: PC_ODR &= ~(1 << CSN);
      0080CF AE 50 0A         [ 2]  243 	ldw	x, #0x500a
      0080D2 F6               [ 1]  244 	ld	a, (x)
      0080D3 A4 F7            [ 1]  245 	and	a, #0xf7
      0080D5 F7               [ 1]  246 	ld	(x), a
                                    247 ;	se8r01-receive-pwm.c: 66: ret = write_spi (reg);
      0080D6 7B 04            [ 1]  248 	ld	a, (0x04, sp)
      0080D8 88               [ 1]  249 	push	a
      0080D9 CD 80 A8         [ 4]  250 	call	_write_spi
      0080DC 5B 01            [ 2]  251 	addw	sp, #1
      0080DE 6B 01            [ 1]  252 	ld	(0x01, sp), a
                                    253 ;	se8r01-receive-pwm.c: 67: if (reg != NOP && reg != FLUSH_RX && reg != FLUSH_TX)
      0080E0 7B 04            [ 1]  254 	ld	a, (0x04, sp)
      0080E2 A1 FF            [ 1]  255 	cp	a, #0xff
      0080E4 27 15            [ 1]  256 	jreq	00102$
      0080E6 7B 04            [ 1]  257 	ld	a, (0x04, sp)
      0080E8 A1 E2            [ 1]  258 	cp	a, #0xe2
      0080EA 27 0F            [ 1]  259 	jreq	00102$
      0080EC 7B 04            [ 1]  260 	ld	a, (0x04, sp)
      0080EE A1 E1            [ 1]  261 	cp	a, #0xe1
      0080F0 27 09            [ 1]  262 	jreq	00102$
                                    263 ;	se8r01-receive-pwm.c: 68: write_spi (value);
      0080F2 7B 05            [ 1]  264 	ld	a, (0x05, sp)
      0080F4 88               [ 1]  265 	push	a
      0080F5 CD 80 A8         [ 4]  266 	call	_write_spi
      0080F8 84               [ 1]  267 	pop	a
      0080F9 20 03            [ 2]  268 	jra	00103$
      0080FB                        269 00102$:
                                    270 ;	se8r01-receive-pwm.c: 70: delayTenMicro ();
      0080FB CD 80 A0         [ 4]  271 	call	_delayTenMicro
      0080FE                        272 00103$:
                                    273 ;	se8r01-receive-pwm.c: 71: PC_ODR |= (1 << CSN);
      0080FE AE 50 0A         [ 2]  274 	ldw	x, #0x500a
      008101 F6               [ 1]  275 	ld	a, (x)
      008102 AA 08            [ 1]  276 	or	a, #0x08
      008104 F7               [ 1]  277 	ld	(x), a
                                    278 ;	se8r01-receive-pwm.c: 72: return (ret);
      008105 7B 01            [ 1]  279 	ld	a, (0x01, sp)
      008107 5B 01            [ 2]  280 	addw	sp, #1
      008109 81               [ 4]  281 	ret
                                    282 ;	se8r01-receive-pwm.c: 74: UCHAR read_spi_reg (UCHAR reg) {
                                    283 ;	-----------------------------------------
                                    284 ;	 function read_spi_reg
                                    285 ;	-----------------------------------------
      00810A                        286 _read_spi_reg:
      00810A 88               [ 1]  287 	push	a
                                    288 ;	se8r01-receive-pwm.c: 76: PC_ODR &= ~(1 << CSN);
      00810B AE 50 0A         [ 2]  289 	ldw	x, #0x500a
      00810E F6               [ 1]  290 	ld	a, (x)
      00810F A4 F7            [ 1]  291 	and	a, #0xf7
      008111 F7               [ 1]  292 	ld	(x), a
                                    293 ;	se8r01-receive-pwm.c: 77: ret = write_spi (reg);
      008112 7B 04            [ 1]  294 	ld	a, (0x04, sp)
      008114 88               [ 1]  295 	push	a
      008115 CD 80 A8         [ 4]  296 	call	_write_spi
      008118 5B 01            [ 2]  297 	addw	sp, #1
      00811A 6B 01            [ 1]  298 	ld	(0x01, sp), a
                                    299 ;	se8r01-receive-pwm.c: 78: if (reg != NOP && reg != FLUSH_RX && reg != FLUSH_TX)
      00811C 7B 04            [ 1]  300 	ld	a, (0x04, sp)
      00811E A1 FF            [ 1]  301 	cp	a, #0xff
      008120 27 17            [ 1]  302 	jreq	00102$
      008122 7B 04            [ 1]  303 	ld	a, (0x04, sp)
      008124 A1 E2            [ 1]  304 	cp	a, #0xe2
      008126 27 11            [ 1]  305 	jreq	00102$
      008128 7B 04            [ 1]  306 	ld	a, (0x04, sp)
      00812A A1 E1            [ 1]  307 	cp	a, #0xe1
      00812C 27 0B            [ 1]  308 	jreq	00102$
                                    309 ;	se8r01-receive-pwm.c: 79: ret = write_spi (NOP);
      00812E 4B FF            [ 1]  310 	push	#0xff
      008130 CD 80 A8         [ 4]  311 	call	_write_spi
      008133 5B 01            [ 2]  312 	addw	sp, #1
      008135 6B 01            [ 1]  313 	ld	(0x01, sp), a
      008137 20 03            [ 2]  314 	jra	00103$
      008139                        315 00102$:
                                    316 ;	se8r01-receive-pwm.c: 81: delayTenMicro ();
      008139 CD 80 A0         [ 4]  317 	call	_delayTenMicro
      00813C                        318 00103$:
                                    319 ;	se8r01-receive-pwm.c: 82: PC_ODR |= (1 << CSN);
      00813C AE 50 0A         [ 2]  320 	ldw	x, #0x500a
      00813F F6               [ 1]  321 	ld	a, (x)
      008140 AA 08            [ 1]  322 	or	a, #0x08
      008142 F7               [ 1]  323 	ld	(x), a
                                    324 ;	se8r01-receive-pwm.c: 83: return (ret);
      008143 7B 01            [ 1]  325 	ld	a, (0x01, sp)
      008145 5B 01            [ 2]  326 	addw	sp, #1
      008147 81               [ 4]  327 	ret
                                    328 ;	se8r01-receive-pwm.c: 85: UCHAR write_spi_buf (UCHAR reg, UCHAR *array, UCHAR len) {
                                    329 ;	-----------------------------------------
                                    330 ;	 function write_spi_buf
                                    331 ;	-----------------------------------------
      008148                        332 _write_spi_buf:
      008148 52 02            [ 2]  333 	sub	sp, #2
                                    334 ;	se8r01-receive-pwm.c: 87: PC_ODR &= ~(1 << CSN);
      00814A AE 50 0A         [ 2]  335 	ldw	x, #0x500a
      00814D F6               [ 1]  336 	ld	a, (x)
      00814E A4 F7            [ 1]  337 	and	a, #0xf7
      008150 F7               [ 1]  338 	ld	(x), a
                                    339 ;	se8r01-receive-pwm.c: 88: ret = write_spi (reg);
      008151 7B 05            [ 1]  340 	ld	a, (0x05, sp)
      008153 88               [ 1]  341 	push	a
      008154 CD 80 A8         [ 4]  342 	call	_write_spi
      008157 5B 01            [ 2]  343 	addw	sp, #1
      008159 6B 02            [ 1]  344 	ld	(0x02, sp), a
                                    345 ;	se8r01-receive-pwm.c: 89: for (n = 0; n < len; ++n)
      00815B 0F 01            [ 1]  346 	clr	(0x01, sp)
      00815D                        347 00103$:
      00815D 7B 01            [ 1]  348 	ld	a, (0x01, sp)
      00815F 11 08            [ 1]  349 	cp	a, (0x08, sp)
      008161 24 11            [ 1]  350 	jrnc	00101$
                                    351 ;	se8r01-receive-pwm.c: 90: write_spi (array[n]);
      008163 5F               [ 1]  352 	clrw	x
      008164 7B 01            [ 1]  353 	ld	a, (0x01, sp)
      008166 97               [ 1]  354 	ld	xl, a
      008167 72 FB 06         [ 2]  355 	addw	x, (0x06, sp)
      00816A F6               [ 1]  356 	ld	a, (x)
      00816B 88               [ 1]  357 	push	a
      00816C CD 80 A8         [ 4]  358 	call	_write_spi
      00816F 84               [ 1]  359 	pop	a
                                    360 ;	se8r01-receive-pwm.c: 89: for (n = 0; n < len; ++n)
      008170 0C 01            [ 1]  361 	inc	(0x01, sp)
      008172 20 E9            [ 2]  362 	jra	00103$
      008174                        363 00101$:
                                    364 ;	se8r01-receive-pwm.c: 91: PC_ODR |= (1 << CSN);
      008174 AE 50 0A         [ 2]  365 	ldw	x, #0x500a
      008177 F6               [ 1]  366 	ld	a, (x)
      008178 AA 08            [ 1]  367 	or	a, #0x08
      00817A F7               [ 1]  368 	ld	(x), a
                                    369 ;	se8r01-receive-pwm.c: 92: return (ret);
      00817B 7B 02            [ 1]  370 	ld	a, (0x02, sp)
      00817D 5B 02            [ 2]  371 	addw	sp, #2
      00817F 81               [ 4]  372 	ret
                                    373 ;	se8r01-receive-pwm.c: 94: UCHAR read_spi_buf (UCHAR reg, UCHAR *array, UCHAR len) {
                                    374 ;	-----------------------------------------
                                    375 ;	 function read_spi_buf
                                    376 ;	-----------------------------------------
      008180                        377 _read_spi_buf:
      008180 52 02            [ 2]  378 	sub	sp, #2
                                    379 ;	se8r01-receive-pwm.c: 96: PC_ODR &= ~(1 << CSN);
      008182 AE 50 0A         [ 2]  380 	ldw	x, #0x500a
      008185 F6               [ 1]  381 	ld	a, (x)
      008186 A4 F7            [ 1]  382 	and	a, #0xf7
      008188 F7               [ 1]  383 	ld	(x), a
                                    384 ;	se8r01-receive-pwm.c: 97: ret = write_spi (reg);
      008189 7B 05            [ 1]  385 	ld	a, (0x05, sp)
      00818B 88               [ 1]  386 	push	a
      00818C CD 80 A8         [ 4]  387 	call	_write_spi
      00818F 5B 01            [ 2]  388 	addw	sp, #1
      008191 6B 01            [ 1]  389 	ld	(0x01, sp), a
                                    390 ;	se8r01-receive-pwm.c: 98: for (n = 0; n < len; ++n)
      008193 0F 02            [ 1]  391 	clr	(0x02, sp)
      008195                        392 00103$:
      008195 7B 02            [ 1]  393 	ld	a, (0x02, sp)
      008197 11 08            [ 1]  394 	cp	a, (0x08, sp)
      008199 24 15            [ 1]  395 	jrnc	00101$
                                    396 ;	se8r01-receive-pwm.c: 99: array[n] = write_spi (NOP);
      00819B 5F               [ 1]  397 	clrw	x
      00819C 7B 02            [ 1]  398 	ld	a, (0x02, sp)
      00819E 97               [ 1]  399 	ld	xl, a
      00819F 72 FB 06         [ 2]  400 	addw	x, (0x06, sp)
      0081A2 89               [ 2]  401 	pushw	x
      0081A3 4B FF            [ 1]  402 	push	#0xff
      0081A5 CD 80 A8         [ 4]  403 	call	_write_spi
      0081A8 5B 01            [ 2]  404 	addw	sp, #1
      0081AA 85               [ 2]  405 	popw	x
      0081AB F7               [ 1]  406 	ld	(x), a
                                    407 ;	se8r01-receive-pwm.c: 98: for (n = 0; n < len; ++n)
      0081AC 0C 02            [ 1]  408 	inc	(0x02, sp)
      0081AE 20 E5            [ 2]  409 	jra	00103$
      0081B0                        410 00101$:
                                    411 ;	se8r01-receive-pwm.c: 100: PC_ODR |= (1 << CSN);
      0081B0 AE 50 0A         [ 2]  412 	ldw	x, #0x500a
      0081B3 F6               [ 1]  413 	ld	a, (x)
      0081B4 AA 08            [ 1]  414 	or	a, #0x08
      0081B6 F7               [ 1]  415 	ld	(x), a
                                    416 ;	se8r01-receive-pwm.c: 101: return (ret);
      0081B7 7B 01            [ 1]  417 	ld	a, (0x01, sp)
      0081B9 5B 02            [ 2]  418 	addw	sp, #2
      0081BB 81               [ 4]  419 	ret
                                    420 ;	se8r01-receive-pwm.c: 103: void InitializeSPI () {
                                    421 ;	-----------------------------------------
                                    422 ;	 function InitializeSPI
                                    423 ;	-----------------------------------------
      0081BC                        424 _InitializeSPI:
                                    425 ;	se8r01-receive-pwm.c: 104: SPI_CR1 = MSBFIRST | SPI_ENABLE | BR_DIV256 | MASTER | CPOL0 | CPHA0;
      0081BC AE 52 00         [ 2]  426 	ldw	x, #0x5200
      0081BF A6 7C            [ 1]  427 	ld	a, #0x7c
      0081C1 F7               [ 1]  428 	ld	(x), a
                                    429 ;	se8r01-receive-pwm.c: 105: SPI_CR2 = BDM_2LINE | CRCEN_OFF | CRCNEXT_TXBUF | FULL_DUPLEX | SSM_DISABLE;
      0081C2 AE 52 01         [ 2]  430 	ldw	x, #0x5201
      0081C5 7F               [ 1]  431 	clr	(x)
                                    432 ;	se8r01-receive-pwm.c: 106: SPI_ICR = TXIE_MASKED | RXIE_MASKED | ERRIE_MASKED | WKIE_MASKED;
      0081C6 AE 52 02         [ 2]  433 	ldw	x, #0x5202
      0081C9 7F               [ 1]  434 	clr	(x)
                                    435 ;	se8r01-receive-pwm.c: 107: PC_DDR = (1 << PC3) | (1 << PC4); // output mode
      0081CA AE 50 0C         [ 2]  436 	ldw	x, #0x500c
      0081CD A6 18            [ 1]  437 	ld	a, #0x18
      0081CF F7               [ 1]  438 	ld	(x), a
                                    439 ;	se8r01-receive-pwm.c: 108: PC_CR1 = (1 << PC3) | (1 << PC4); // push-pull
      0081D0 AE 50 0D         [ 2]  440 	ldw	x, #0x500d
      0081D3 A6 18            [ 1]  441 	ld	a, #0x18
      0081D5 F7               [ 1]  442 	ld	(x), a
                                    443 ;	se8r01-receive-pwm.c: 109: PC_CR2 = (1 << PC3) | (1 << PC4); // up to 10MHz speed
      0081D6 AE 50 0E         [ 2]  444 	ldw	x, #0x500e
      0081D9 A6 18            [ 1]  445 	ld	a, #0x18
      0081DB F7               [ 1]  446 	ld	(x), a
                                    447 ;	se8r01-receive-pwm.c: 111: PC_ODR &= ~(1 << CE);
      0081DC AE 50 0A         [ 2]  448 	ldw	x, #0x500a
      0081DF F6               [ 1]  449 	ld	a, (x)
      0081E0 A4 EF            [ 1]  450 	and	a, #0xef
      0081E2 F7               [ 1]  451 	ld	(x), a
      0081E3 81               [ 4]  452 	ret
                                    453 ;	se8r01-receive-pwm.c: 113: void InitializeSystemClock() {
                                    454 ;	-----------------------------------------
                                    455 ;	 function InitializeSystemClock
                                    456 ;	-----------------------------------------
      0081E4                        457 _InitializeSystemClock:
                                    458 ;	se8r01-receive-pwm.c: 114: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0081E4 AE 50 C0         [ 2]  459 	ldw	x, #0x50c0
      0081E7 7F               [ 1]  460 	clr	(x)
                                    461 ;	se8r01-receive-pwm.c: 115: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0081E8 AE 50 C0         [ 2]  462 	ldw	x, #0x50c0
      0081EB A6 01            [ 1]  463 	ld	a, #0x01
      0081ED F7               [ 1]  464 	ld	(x), a
                                    465 ;	se8r01-receive-pwm.c: 116: CLK_ECKR = 0;                       //  Disable the external clock.
      0081EE AE 50 C1         [ 2]  466 	ldw	x, #0x50c1
      0081F1 7F               [ 1]  467 	clr	(x)
                                    468 ;	se8r01-receive-pwm.c: 117: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0081F2                        469 00101$:
      0081F2 AE 50 C0         [ 2]  470 	ldw	x, #0x50c0
      0081F5 F6               [ 1]  471 	ld	a, (x)
      0081F6 A5 02            [ 1]  472 	bcp	a, #0x02
      0081F8 27 F8            [ 1]  473 	jreq	00101$
                                    474 ;	se8r01-receive-pwm.c: 118: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0081FA AE 50 C6         [ 2]  475 	ldw	x, #0x50c6
      0081FD 7F               [ 1]  476 	clr	(x)
                                    477 ;	se8r01-receive-pwm.c: 119: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0081FE AE 50 C7         [ 2]  478 	ldw	x, #0x50c7
      008201 A6 FF            [ 1]  479 	ld	a, #0xff
      008203 F7               [ 1]  480 	ld	(x), a
                                    481 ;	se8r01-receive-pwm.c: 120: CLK_PCKENR2 = 0xff;                 //  Ditto.
      008204 AE 50 CA         [ 2]  482 	ldw	x, #0x50ca
      008207 A6 FF            [ 1]  483 	ld	a, #0xff
      008209 F7               [ 1]  484 	ld	(x), a
                                    485 ;	se8r01-receive-pwm.c: 121: CLK_CCOR = 0;                       //  Turn off CCO.
      00820A AE 50 C9         [ 2]  486 	ldw	x, #0x50c9
      00820D 7F               [ 1]  487 	clr	(x)
                                    488 ;	se8r01-receive-pwm.c: 122: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      00820E AE 50 CC         [ 2]  489 	ldw	x, #0x50cc
      008211 7F               [ 1]  490 	clr	(x)
                                    491 ;	se8r01-receive-pwm.c: 123: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      008212 AE 50 CD         [ 2]  492 	ldw	x, #0x50cd
      008215 7F               [ 1]  493 	clr	(x)
                                    494 ;	se8r01-receive-pwm.c: 124: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      008216 AE 50 C4         [ 2]  495 	ldw	x, #0x50c4
      008219 A6 E1            [ 1]  496 	ld	a, #0xe1
      00821B F7               [ 1]  497 	ld	(x), a
                                    498 ;	se8r01-receive-pwm.c: 125: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      00821C AE 50 C5         [ 2]  499 	ldw	x, #0x50c5
      00821F 7F               [ 1]  500 	clr	(x)
                                    501 ;	se8r01-receive-pwm.c: 126: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      008220 AE 50 C5         [ 2]  502 	ldw	x, #0x50c5
      008223 A6 02            [ 1]  503 	ld	a, #0x02
      008225 F7               [ 1]  504 	ld	(x), a
                                    505 ;	se8r01-receive-pwm.c: 127: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      008226                        506 00104$:
      008226 AE 50 C5         [ 2]  507 	ldw	x, #0x50c5
      008229 F6               [ 1]  508 	ld	a, (x)
      00822A 44               [ 1]  509 	srl	a
      00822B 25 F9            [ 1]  510 	jrc	00104$
      00822D 81               [ 4]  511 	ret
                                    512 ;	se8r01-receive-pwm.c: 129: void delay (int time_ms) {
                                    513 ;	-----------------------------------------
                                    514 ;	 function delay
                                    515 ;	-----------------------------------------
      00822E                        516 _delay:
      00822E 52 0A            [ 2]  517 	sub	sp, #10
                                    518 ;	se8r01-receive-pwm.c: 131: for (x = 0; x < 1036*time_ms; ++x)
      008230 5F               [ 1]  519 	clrw	x
      008231 1F 03            [ 2]  520 	ldw	(0x03, sp), x
      008233 1F 01            [ 2]  521 	ldw	(0x01, sp), x
      008235 1E 0D            [ 2]  522 	ldw	x, (0x0d, sp)
      008237 89               [ 2]  523 	pushw	x
      008238 4B 0C            [ 1]  524 	push	#0x0c
      00823A 4B 04            [ 1]  525 	push	#0x04
      00823C CD 89 43         [ 4]  526 	call	__mulint
      00823F 5B 04            [ 2]  527 	addw	sp, #4
      008241 1F 09            [ 2]  528 	ldw	(0x09, sp), x
      008243                        529 00103$:
      008243 16 09            [ 2]  530 	ldw	y, (0x09, sp)
      008245 17 07            [ 2]  531 	ldw	(0x07, sp), y
      008247 7B 07            [ 1]  532 	ld	a, (0x07, sp)
      008249 49               [ 1]  533 	rlc	a
      00824A 4F               [ 1]  534 	clr	a
      00824B A2 00            [ 1]  535 	sbc	a, #0x00
      00824D 6B 06            [ 1]  536 	ld	(0x06, sp), a
      00824F 6B 05            [ 1]  537 	ld	(0x05, sp), a
      008251 1E 03            [ 2]  538 	ldw	x, (0x03, sp)
      008253 13 07            [ 2]  539 	cpw	x, (0x07, sp)
      008255 7B 02            [ 1]  540 	ld	a, (0x02, sp)
      008257 12 06            [ 1]  541 	sbc	a, (0x06, sp)
      008259 7B 01            [ 1]  542 	ld	a, (0x01, sp)
      00825B 12 05            [ 1]  543 	sbc	a, (0x05, sp)
      00825D 2E 17            [ 1]  544 	jrsge	00105$
                                    545 ;	se8r01-receive-pwm.c: 132: __asm__("nop");
      00825F 9D               [ 1]  546 	nop
                                    547 ;	se8r01-receive-pwm.c: 131: for (x = 0; x < 1036*time_ms; ++x)
      008260 16 03            [ 2]  548 	ldw	y, (0x03, sp)
      008262 72 A9 00 01      [ 2]  549 	addw	y, #0x0001
      008266 7B 02            [ 1]  550 	ld	a, (0x02, sp)
      008268 A9 00            [ 1]  551 	adc	a, #0x00
      00826A 97               [ 1]  552 	ld	xl, a
      00826B 7B 01            [ 1]  553 	ld	a, (0x01, sp)
      00826D A9 00            [ 1]  554 	adc	a, #0x00
      00826F 95               [ 1]  555 	ld	xh, a
      008270 17 03            [ 2]  556 	ldw	(0x03, sp), y
      008272 1F 01            [ 2]  557 	ldw	(0x01, sp), x
      008274 20 CD            [ 2]  558 	jra	00103$
      008276                        559 00105$:
      008276 5B 0A            [ 2]  560 	addw	sp, #10
      008278 81               [ 4]  561 	ret
                                    562 ;	se8r01-receive-pwm.c: 137: void UARTPrintF (char *message) {
                                    563 ;	-----------------------------------------
                                    564 ;	 function UARTPrintF
                                    565 ;	-----------------------------------------
      008279                        566 _UARTPrintF:
                                    567 ;	se8r01-receive-pwm.c: 138: char *ch = message;
      008279 16 03            [ 2]  568 	ldw	y, (0x03, sp)
                                    569 ;	se8r01-receive-pwm.c: 139: while (*ch) {
      00827B                        570 00104$:
      00827B 90 F6            [ 1]  571 	ld	a, (y)
      00827D 4D               [ 1]  572 	tnz	a
      00827E 27 0F            [ 1]  573 	jreq	00107$
                                    574 ;	se8r01-receive-pwm.c: 140: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008280 AE 52 31         [ 2]  575 	ldw	x, #0x5231
      008283 F7               [ 1]  576 	ld	(x), a
                                    577 ;	se8r01-receive-pwm.c: 141: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      008284                        578 00101$:
      008284 AE 52 30         [ 2]  579 	ldw	x, #0x5230
      008287 F6               [ 1]  580 	ld	a, (x)
      008288 48               [ 1]  581 	sll	a
      008289 24 F9            [ 1]  582 	jrnc	00101$
                                    583 ;	se8r01-receive-pwm.c: 142: ch++;                               //  Grab the next character.
      00828B 90 5C            [ 2]  584 	incw	y
      00828D 20 EC            [ 2]  585 	jra	00104$
      00828F                        586 00107$:
      00828F 81               [ 4]  587 	ret
                                    588 ;	se8r01-receive-pwm.c: 145: void print_UCHAR_hex (unsigned char buffer) {
                                    589 ;	-----------------------------------------
                                    590 ;	 function print_UCHAR_hex
                                    591 ;	-----------------------------------------
      008290                        592 _print_UCHAR_hex:
      008290 52 0C            [ 2]  593 	sub	sp, #12
                                    594 ;	se8r01-receive-pwm.c: 148: a = (buffer >> 4);
      008292 7B 0F            [ 1]  595 	ld	a, (0x0f, sp)
      008294 4E               [ 1]  596 	swap	a
      008295 A4 0F            [ 1]  597 	and	a, #0x0f
      008297 5F               [ 1]  598 	clrw	x
      008298 97               [ 1]  599 	ld	xl, a
                                    600 ;	se8r01-receive-pwm.c: 149: if (a > 9)
      008299 A3 00 09         [ 2]  601 	cpw	x, #0x0009
      00829C 2D 07            [ 1]  602 	jrsle	00102$
                                    603 ;	se8r01-receive-pwm.c: 150: a = a + 'a' - 10;
      00829E 1C 00 57         [ 2]  604 	addw	x, #0x0057
      0082A1 1F 0B            [ 2]  605 	ldw	(0x0b, sp), x
      0082A3 20 05            [ 2]  606 	jra	00103$
      0082A5                        607 00102$:
                                    608 ;	se8r01-receive-pwm.c: 152: a += '0'; 
      0082A5 1C 00 30         [ 2]  609 	addw	x, #0x0030
      0082A8 1F 0B            [ 2]  610 	ldw	(0x0b, sp), x
      0082AA                        611 00103$:
                                    612 ;	se8r01-receive-pwm.c: 153: b = buffer & 0x0f;
      0082AA 7B 0F            [ 1]  613 	ld	a, (0x0f, sp)
      0082AC A4 0F            [ 1]  614 	and	a, #0x0f
      0082AE 5F               [ 1]  615 	clrw	x
      0082AF 97               [ 1]  616 	ld	xl, a
                                    617 ;	se8r01-receive-pwm.c: 154: if (b > 9)
      0082B0 A3 00 09         [ 2]  618 	cpw	x, #0x0009
      0082B3 2D 07            [ 1]  619 	jrsle	00105$
                                    620 ;	se8r01-receive-pwm.c: 155: b = b + 'a' - 10;
      0082B5 1C 00 57         [ 2]  621 	addw	x, #0x0057
      0082B8 1F 09            [ 2]  622 	ldw	(0x09, sp), x
      0082BA 20 05            [ 2]  623 	jra	00106$
      0082BC                        624 00105$:
                                    625 ;	se8r01-receive-pwm.c: 157: b += '0'; 
      0082BC 1C 00 30         [ 2]  626 	addw	x, #0x0030
      0082BF 1F 09            [ 2]  627 	ldw	(0x09, sp), x
      0082C1                        628 00106$:
                                    629 ;	se8r01-receive-pwm.c: 158: message[0] = a;
      0082C1 90 96            [ 1]  630 	ldw	y, sp
      0082C3 90 5C            [ 2]  631 	incw	y
      0082C5 7B 0C            [ 1]  632 	ld	a, (0x0c, sp)
      0082C7 90 F7            [ 1]  633 	ld	(y), a
                                    634 ;	se8r01-receive-pwm.c: 159: message[1] = b;
      0082C9 93               [ 1]  635 	ldw	x, y
      0082CA 5C               [ 2]  636 	incw	x
      0082CB 7B 0A            [ 1]  637 	ld	a, (0x0a, sp)
      0082CD F7               [ 1]  638 	ld	(x), a
                                    639 ;	se8r01-receive-pwm.c: 160: message[2] = 0;
      0082CE 93               [ 1]  640 	ldw	x, y
      0082CF 5C               [ 2]  641 	incw	x
      0082D0 5C               [ 2]  642 	incw	x
      0082D1 7F               [ 1]  643 	clr	(x)
                                    644 ;	se8r01-receive-pwm.c: 161: UARTPrintF (message);
      0082D2 90 89            [ 2]  645 	pushw	y
      0082D4 CD 82 79         [ 4]  646 	call	_UARTPrintF
      0082D7 5B 02            [ 2]  647 	addw	sp, #2
      0082D9 5B 0C            [ 2]  648 	addw	sp, #12
      0082DB 81               [ 4]  649 	ret
                                    650 ;	se8r01-receive-pwm.c: 164: void InitializeUART() {
                                    651 ;	-----------------------------------------
                                    652 ;	 function InitializeUART
                                    653 ;	-----------------------------------------
      0082DC                        654 _InitializeUART:
                                    655 ;	se8r01-receive-pwm.c: 174: UART1_CR1 = 0;
      0082DC AE 52 34         [ 2]  656 	ldw	x, #0x5234
      0082DF 7F               [ 1]  657 	clr	(x)
                                    658 ;	se8r01-receive-pwm.c: 175: UART1_CR2 = 0;
      0082E0 AE 52 35         [ 2]  659 	ldw	x, #0x5235
      0082E3 7F               [ 1]  660 	clr	(x)
                                    661 ;	se8r01-receive-pwm.c: 176: UART1_CR4 = 0;
      0082E4 AE 52 37         [ 2]  662 	ldw	x, #0x5237
      0082E7 7F               [ 1]  663 	clr	(x)
                                    664 ;	se8r01-receive-pwm.c: 177: UART1_CR3 = 0;
      0082E8 AE 52 36         [ 2]  665 	ldw	x, #0x5236
      0082EB 7F               [ 1]  666 	clr	(x)
                                    667 ;	se8r01-receive-pwm.c: 178: UART1_CR5 = 0;
      0082EC AE 52 38         [ 2]  668 	ldw	x, #0x5238
      0082EF 7F               [ 1]  669 	clr	(x)
                                    670 ;	se8r01-receive-pwm.c: 179: UART1_GTR = 0;
      0082F0 AE 52 39         [ 2]  671 	ldw	x, #0x5239
      0082F3 7F               [ 1]  672 	clr	(x)
                                    673 ;	se8r01-receive-pwm.c: 180: UART1_PSCR = 0;
      0082F4 AE 52 3A         [ 2]  674 	ldw	x, #0x523a
      0082F7 7F               [ 1]  675 	clr	(x)
                                    676 ;	se8r01-receive-pwm.c: 184: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      0082F8 AE 52 34         [ 2]  677 	ldw	x, #0x5234
      0082FB F6               [ 1]  678 	ld	a, (x)
      0082FC A4 EF            [ 1]  679 	and	a, #0xef
      0082FE F7               [ 1]  680 	ld	(x), a
                                    681 ;	se8r01-receive-pwm.c: 185: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      0082FF AE 52 34         [ 2]  682 	ldw	x, #0x5234
      008302 F6               [ 1]  683 	ld	a, (x)
      008303 A4 FB            [ 1]  684 	and	a, #0xfb
      008305 F7               [ 1]  685 	ld	(x), a
                                    686 ;	se8r01-receive-pwm.c: 186: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      008306 AE 52 36         [ 2]  687 	ldw	x, #0x5236
      008309 F6               [ 1]  688 	ld	a, (x)
      00830A A4 DF            [ 1]  689 	and	a, #0xdf
      00830C F7               [ 1]  690 	ld	(x), a
                                    691 ;	se8r01-receive-pwm.c: 187: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      00830D AE 52 36         [ 2]  692 	ldw	x, #0x5236
      008310 F6               [ 1]  693 	ld	a, (x)
      008311 A4 EF            [ 1]  694 	and	a, #0xef
      008313 F7               [ 1]  695 	ld	(x), a
                                    696 ;	se8r01-receive-pwm.c: 188: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      008314 AE 52 33         [ 2]  697 	ldw	x, #0x5233
      008317 A6 0A            [ 1]  698 	ld	a, #0x0a
      008319 F7               [ 1]  699 	ld	(x), a
                                    700 ;	se8r01-receive-pwm.c: 189: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      00831A AE 52 32         [ 2]  701 	ldw	x, #0x5232
      00831D A6 08            [ 1]  702 	ld	a, #0x08
      00831F F7               [ 1]  703 	ld	(x), a
                                    704 ;	se8r01-receive-pwm.c: 193: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      008320 AE 52 35         [ 2]  705 	ldw	x, #0x5235
      008323 F6               [ 1]  706 	ld	a, (x)
      008324 A4 F7            [ 1]  707 	and	a, #0xf7
      008326 F7               [ 1]  708 	ld	(x), a
                                    709 ;	se8r01-receive-pwm.c: 194: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      008327 AE 52 35         [ 2]  710 	ldw	x, #0x5235
      00832A F6               [ 1]  711 	ld	a, (x)
      00832B A4 FB            [ 1]  712 	and	a, #0xfb
      00832D F7               [ 1]  713 	ld	(x), a
                                    714 ;	se8r01-receive-pwm.c: 198: SET (UART1_CR3, CR3_CPOL);
      00832E AE 52 36         [ 2]  715 	ldw	x, #0x5236
      008331 F6               [ 1]  716 	ld	a, (x)
      008332 AA 04            [ 1]  717 	or	a, #0x04
      008334 F7               [ 1]  718 	ld	(x), a
                                    719 ;	se8r01-receive-pwm.c: 199: SET (UART1_CR3, CR3_CPHA);
      008335 AE 52 36         [ 2]  720 	ldw	x, #0x5236
      008338 F6               [ 1]  721 	ld	a, (x)
      008339 AA 02            [ 1]  722 	or	a, #0x02
      00833B F7               [ 1]  723 	ld	(x), a
                                    724 ;	se8r01-receive-pwm.c: 200: SET (UART1_CR3, CR3_LBCL);
      00833C 72 10 52 36      [ 1]  725 	bset	0x5236, #0
                                    726 ;	se8r01-receive-pwm.c: 204: SET (UART1_CR2, CR2_TEN);
      008340 AE 52 35         [ 2]  727 	ldw	x, #0x5235
      008343 F6               [ 1]  728 	ld	a, (x)
      008344 AA 08            [ 1]  729 	or	a, #0x08
      008346 F7               [ 1]  730 	ld	(x), a
                                    731 ;	se8r01-receive-pwm.c: 205: SET (UART1_CR2, CR2_REN);
      008347 AE 52 35         [ 2]  732 	ldw	x, #0x5235
      00834A F6               [ 1]  733 	ld	a, (x)
      00834B AA 04            [ 1]  734 	or	a, #0x04
      00834D F7               [ 1]  735 	ld	(x), a
                                    736 ;	se8r01-receive-pwm.c: 206: UART1_CR3 = CR3_CLKEN;
      00834E AE 52 36         [ 2]  737 	ldw	x, #0x5236
      008351 A6 08            [ 1]  738 	ld	a, #0x08
      008353 F7               [ 1]  739 	ld	(x), a
      008354 81               [ 4]  740 	ret
                                    741 ;	se8r01-receive-pwm.c: 279: void init_io(void)
                                    742 ;	-----------------------------------------
                                    743 ;	 function init_io
                                    744 ;	-----------------------------------------
      008355                        745 _init_io:
                                    746 ;	se8r01-receive-pwm.c: 281: PD_DDR &= ~(1 << 3); // input mode
      008355 AE 50 11         [ 2]  747 	ldw	x, #0x5011
      008358 F6               [ 1]  748 	ld	a, (x)
      008359 A4 F7            [ 1]  749 	and	a, #0xf7
      00835B F7               [ 1]  750 	ld	(x), a
                                    751 ;	se8r01-receive-pwm.c: 282: PD_CR1 |= (1 << 3); // input with pull up 
      00835C AE 50 12         [ 2]  752 	ldw	x, #0x5012
      00835F F6               [ 1]  753 	ld	a, (x)
      008360 AA 08            [ 1]  754 	or	a, #0x08
      008362 F7               [ 1]  755 	ld	(x), a
                                    756 ;	se8r01-receive-pwm.c: 283: PD_CR2 |= (1 << 3); // interrupt enabled 
      008363 AE 50 13         [ 2]  757 	ldw	x, #0x5013
      008366 F6               [ 1]  758 	ld	a, (x)
      008367 AA 08            [ 1]  759 	or	a, #0x08
      008369 F7               [ 1]  760 	ld	(x), a
                                    761 ;	se8r01-receive-pwm.c: 287: PC_ODR &= ~(1 << CE);
      00836A AE 50 0A         [ 2]  762 	ldw	x, #0x500a
      00836D F6               [ 1]  763 	ld	a, (x)
      00836E A4 EF            [ 1]  764 	and	a, #0xef
      008370 F7               [ 1]  765 	ld	(x), a
                                    766 ;	se8r01-receive-pwm.c: 289: PC_ODR |= (1 << CSN);
      008371 AE 50 0A         [ 2]  767 	ldw	x, #0x500a
      008374 F6               [ 1]  768 	ld	a, (x)
      008375 AA 08            [ 1]  769 	or	a, #0x08
      008377 F7               [ 1]  770 	ld	(x), a
      008378 81               [ 4]  771 	ret
                                    772 ;	se8r01-receive-pwm.c: 295: void rf_switch_bank(unsigned char bankindex)
                                    773 ;	-----------------------------------------
                                    774 ;	 function rf_switch_bank
                                    775 ;	-----------------------------------------
      008379                        776 _rf_switch_bank:
      008379 88               [ 1]  777 	push	a
                                    778 ;	se8r01-receive-pwm.c: 298: temp1 = bankindex;
      00837A 7B 04            [ 1]  779 	ld	a, (0x04, sp)
      00837C 6B 01            [ 1]  780 	ld	(0x01, sp), a
                                    781 ;	se8r01-receive-pwm.c: 300: temp0 = write_spi(iRF_BANK0_STATUS);
      00837E 4B 07            [ 1]  782 	push	#0x07
      008380 CD 80 A8         [ 4]  783 	call	_write_spi
      008383 5B 01            [ 2]  784 	addw	sp, #1
                                    785 ;	se8r01-receive-pwm.c: 302: if((temp0&0x80)!=temp1)
      008385 A4 80            [ 1]  786 	and	a, #0x80
      008387 11 01            [ 1]  787 	cp	a, (0x01, sp)
      008389 27 09            [ 1]  788 	jreq	00103$
                                    789 ;	se8r01-receive-pwm.c: 304: write_spi_reg(iRF_CMD_ACTIVATE,0x53);
      00838B 4B 53            [ 1]  790 	push	#0x53
      00838D 4B 50            [ 1]  791 	push	#0x50
      00838F CD 80 CE         [ 4]  792 	call	_write_spi_reg
      008392 5B 02            [ 2]  793 	addw	sp, #2
      008394                        794 00103$:
      008394 84               [ 1]  795 	pop	a
      008395 81               [ 4]  796 	ret
                                    797 ;	se8r01-receive-pwm.c: 311: void SE8R01_Calibration()
                                    798 ;	-----------------------------------------
                                    799 ;	 function SE8R01_Calibration
                                    800 ;	-----------------------------------------
      008396                        801 _SE8R01_Calibration:
      008396 52 0D            [ 2]  802 	sub	sp, #13
                                    803 ;	se8r01-receive-pwm.c: 314: rf_switch_bank(iBANK0);
      008398 4B 00            [ 1]  804 	push	#0x00
      00839A CD 83 79         [ 4]  805 	call	_rf_switch_bank
      00839D 84               [ 1]  806 	pop	a
                                    807 ;	se8r01-receive-pwm.c: 315: temp[0]=0x03;
      00839E 96               [ 1]  808 	ldw	x, sp
      00839F 5C               [ 2]  809 	incw	x
      0083A0 1F 06            [ 2]  810 	ldw	(0x06, sp), x
      0083A2 1E 06            [ 2]  811 	ldw	x, (0x06, sp)
      0083A4 A6 03            [ 1]  812 	ld	a, #0x03
      0083A6 F7               [ 1]  813 	ld	(x), a
                                    814 ;	se8r01-receive-pwm.c: 316: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_CONFIG,temp, 1);
      0083A7 1E 06            [ 2]  815 	ldw	x, (0x06, sp)
      0083A9 4B 01            [ 1]  816 	push	#0x01
      0083AB 89               [ 2]  817 	pushw	x
      0083AC 4B 20            [ 1]  818 	push	#0x20
      0083AE CD 81 48         [ 4]  819 	call	_write_spi_buf
      0083B1 5B 04            [ 2]  820 	addw	sp, #4
                                    821 ;	se8r01-receive-pwm.c: 318: temp[0]=0x32;
      0083B3 1E 06            [ 2]  822 	ldw	x, (0x06, sp)
      0083B5 A6 32            [ 1]  823 	ld	a, #0x32
      0083B7 F7               [ 1]  824 	ld	(x), a
                                    825 ;	se8r01-receive-pwm.c: 320: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_CH, temp,1);
      0083B8 1E 06            [ 2]  826 	ldw	x, (0x06, sp)
      0083BA 4B 01            [ 1]  827 	push	#0x01
      0083BC 89               [ 2]  828 	pushw	x
      0083BD 4B 25            [ 1]  829 	push	#0x25
      0083BF CD 81 48         [ 4]  830 	call	_write_spi_buf
      0083C2 5B 04            [ 2]  831 	addw	sp, #4
                                    832 ;	se8r01-receive-pwm.c: 324: if (SE8R01_DR_2M==1)
      0083C4 CE 00 10         [ 2]  833 	ldw	x, _SE8R01_DR_2M+0
      0083C7 A3 00 01         [ 2]  834 	cpw	x, #0x0001
      0083CA 26 07            [ 1]  835 	jrne	00105$
                                    836 ;	se8r01-receive-pwm.c: 325: {temp[0]=0x48;}
      0083CC 1E 06            [ 2]  837 	ldw	x, (0x06, sp)
      0083CE A6 48            [ 1]  838 	ld	a, #0x48
      0083D0 F7               [ 1]  839 	ld	(x), a
      0083D1 20 14            [ 2]  840 	jra	00106$
      0083D3                        841 00105$:
                                    842 ;	se8r01-receive-pwm.c: 326: else if (SE8R01_DR_1M==1)
      0083D3 CE 00 12         [ 2]  843 	ldw	x, _SE8R01_DR_1M+0
      0083D6 A3 00 01         [ 2]  844 	cpw	x, #0x0001
      0083D9 26 07            [ 1]  845 	jrne	00102$
                                    846 ;	se8r01-receive-pwm.c: 327: {temp[0]=0x40;}
      0083DB 1E 06            [ 2]  847 	ldw	x, (0x06, sp)
      0083DD A6 40            [ 1]  848 	ld	a, #0x40
      0083DF F7               [ 1]  849 	ld	(x), a
      0083E0 20 05            [ 2]  850 	jra	00106$
      0083E2                        851 00102$:
                                    852 ;	se8r01-receive-pwm.c: 329: {temp[0]=0x68;}   
      0083E2 1E 06            [ 2]  853 	ldw	x, (0x06, sp)
      0083E4 A6 68            [ 1]  854 	ld	a, #0x68
      0083E6 F7               [ 1]  855 	ld	(x), a
      0083E7                        856 00106$:
                                    857 ;	se8r01-receive-pwm.c: 331: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_SETUP,temp,1);
      0083E7 1E 06            [ 2]  858 	ldw	x, (0x06, sp)
      0083E9 4B 01            [ 1]  859 	push	#0x01
      0083EB 89               [ 2]  860 	pushw	x
      0083EC 4B 26            [ 1]  861 	push	#0x26
      0083EE CD 81 48         [ 4]  862 	call	_write_spi_buf
      0083F1 5B 04            [ 2]  863 	addw	sp, #4
                                    864 ;	se8r01-receive-pwm.c: 332: temp[0]=0x77;
      0083F3 1E 06            [ 2]  865 	ldw	x, (0x06, sp)
      0083F5 A6 77            [ 1]  866 	ld	a, #0x77
      0083F7 F7               [ 1]  867 	ld	(x), a
                                    868 ;	se8r01-receive-pwm.c: 333: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_PRE_GURD, temp,1);
      0083F8 1E 06            [ 2]  869 	ldw	x, (0x06, sp)
      0083FA 4B 01            [ 1]  870 	push	#0x01
      0083FC 89               [ 2]  871 	pushw	x
      0083FD 4B 3F            [ 1]  872 	push	#0x3f
      0083FF CD 81 48         [ 4]  873 	call	_write_spi_buf
      008402 5B 04            [ 2]  874 	addw	sp, #4
                                    875 ;	se8r01-receive-pwm.c: 335: rf_switch_bank(iBANK1);
      008404 4B 80            [ 1]  876 	push	#0x80
      008406 CD 83 79         [ 4]  877 	call	_rf_switch_bank
      008409 84               [ 1]  878 	pop	a
                                    879 ;	se8r01-receive-pwm.c: 336: temp[0]=0x40;
      00840A 1E 06            [ 2]  880 	ldw	x, (0x06, sp)
      00840C A6 40            [ 1]  881 	ld	a, #0x40
      00840E F7               [ 1]  882 	ld	(x), a
                                    883 ;	se8r01-receive-pwm.c: 337: temp[1]=0x00;
      00840F 1E 06            [ 2]  884 	ldw	x, (0x06, sp)
      008411 5C               [ 2]  885 	incw	x
      008412 1F 0C            [ 2]  886 	ldw	(0x0c, sp), x
      008414 1E 0C            [ 2]  887 	ldw	x, (0x0c, sp)
      008416 7F               [ 1]  888 	clr	(x)
                                    889 ;	se8r01-receive-pwm.c: 338: temp[2]=0x10;
      008417 1E 06            [ 2]  890 	ldw	x, (0x06, sp)
      008419 5C               [ 2]  891 	incw	x
      00841A 5C               [ 2]  892 	incw	x
      00841B 1F 0A            [ 2]  893 	ldw	(0x0a, sp), x
      00841D 1E 0A            [ 2]  894 	ldw	x, (0x0a, sp)
      00841F A6 10            [ 1]  895 	ld	a, #0x10
      008421 F7               [ 1]  896 	ld	(x), a
                                    897 ;	se8r01-receive-pwm.c: 340: {temp[3]=0xE6;}
      008422 1E 06            [ 2]  898 	ldw	x, (0x06, sp)
      008424 1C 00 03         [ 2]  899 	addw	x, #0x0003
      008427 1F 08            [ 2]  900 	ldw	(0x08, sp), x
                                    901 ;	se8r01-receive-pwm.c: 339: if (SE8R01_DR_2M==1)
      008429 CE 00 10         [ 2]  902 	ldw	x, _SE8R01_DR_2M+0
      00842C A3 00 01         [ 2]  903 	cpw	x, #0x0001
      00842F 26 07            [ 1]  904 	jrne	00108$
                                    905 ;	se8r01-receive-pwm.c: 340: {temp[3]=0xE6;}
      008431 1E 08            [ 2]  906 	ldw	x, (0x08, sp)
      008433 A6 E6            [ 1]  907 	ld	a, #0xe6
      008435 F7               [ 1]  908 	ld	(x), a
      008436 20 05            [ 2]  909 	jra	00109$
      008438                        910 00108$:
                                    911 ;	se8r01-receive-pwm.c: 342: {temp[3]=0xE4;}
      008438 1E 08            [ 2]  912 	ldw	x, (0x08, sp)
      00843A A6 E4            [ 1]  913 	ld	a, #0xe4
      00843C F7               [ 1]  914 	ld	(x), a
      00843D                        915 00109$:
                                    916 ;	se8r01-receive-pwm.c: 344: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_PLL_CTL0, temp, 4);
      00843D 1E 06            [ 2]  917 	ldw	x, (0x06, sp)
      00843F 4B 04            [ 1]  918 	push	#0x04
      008441 89               [ 2]  919 	pushw	x
      008442 4B 21            [ 1]  920 	push	#0x21
      008444 CD 81 48         [ 4]  921 	call	_write_spi_buf
      008447 5B 04            [ 2]  922 	addw	sp, #4
                                    923 ;	se8r01-receive-pwm.c: 346: temp[0]=0x20;
      008449 1E 06            [ 2]  924 	ldw	x, (0x06, sp)
      00844B A6 20            [ 1]  925 	ld	a, #0x20
      00844D F7               [ 1]  926 	ld	(x), a
                                    927 ;	se8r01-receive-pwm.c: 347: temp[1]=0x08;
      00844E 1E 0C            [ 2]  928 	ldw	x, (0x0c, sp)
      008450 A6 08            [ 1]  929 	ld	a, #0x08
      008452 F7               [ 1]  930 	ld	(x), a
                                    931 ;	se8r01-receive-pwm.c: 348: temp[2]=0x50;
      008453 1E 0A            [ 2]  932 	ldw	x, (0x0a, sp)
      008455 A6 50            [ 1]  933 	ld	a, #0x50
      008457 F7               [ 1]  934 	ld	(x), a
                                    935 ;	se8r01-receive-pwm.c: 349: temp[3]=0x40;
      008458 1E 08            [ 2]  936 	ldw	x, (0x08, sp)
      00845A A6 40            [ 1]  937 	ld	a, #0x40
      00845C F7               [ 1]  938 	ld	(x), a
                                    939 ;	se8r01-receive-pwm.c: 350: temp[4]=0x50;
      00845D 1E 06            [ 2]  940 	ldw	x, (0x06, sp)
      00845F A6 50            [ 1]  941 	ld	a, #0x50
      008461 E7 04            [ 1]  942 	ld	(0x0004, x), a
                                    943 ;	se8r01-receive-pwm.c: 351: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_CAL_CTL, temp, 5);
      008463 1E 06            [ 2]  944 	ldw	x, (0x06, sp)
      008465 4B 05            [ 1]  945 	push	#0x05
      008467 89               [ 2]  946 	pushw	x
      008468 4B 23            [ 1]  947 	push	#0x23
      00846A CD 81 48         [ 4]  948 	call	_write_spi_buf
      00846D 5B 04            [ 2]  949 	addw	sp, #4
                                    950 ;	se8r01-receive-pwm.c: 353: temp[0]=0x00;
      00846F 1E 06            [ 2]  951 	ldw	x, (0x06, sp)
      008471 7F               [ 1]  952 	clr	(x)
                                    953 ;	se8r01-receive-pwm.c: 354: temp[1]=0x00;
      008472 1E 0C            [ 2]  954 	ldw	x, (0x0c, sp)
      008474 7F               [ 1]  955 	clr	(x)
                                    956 ;	se8r01-receive-pwm.c: 355: if (SE8R01_DR_2M==1)
      008475 CE 00 10         [ 2]  957 	ldw	x, _SE8R01_DR_2M+0
      008478 A3 00 01         [ 2]  958 	cpw	x, #0x0001
      00847B 26 07            [ 1]  959 	jrne	00111$
                                    960 ;	se8r01-receive-pwm.c: 356: { temp[2]=0x1E;}
      00847D 1E 0A            [ 2]  961 	ldw	x, (0x0a, sp)
      00847F A6 1E            [ 1]  962 	ld	a, #0x1e
      008481 F7               [ 1]  963 	ld	(x), a
      008482 20 05            [ 2]  964 	jra	00112$
      008484                        965 00111$:
                                    966 ;	se8r01-receive-pwm.c: 358: { temp[2]=0x1F;}
      008484 1E 0A            [ 2]  967 	ldw	x, (0x0a, sp)
      008486 A6 1F            [ 1]  968 	ld	a, #0x1f
      008488 F7               [ 1]  969 	ld	(x), a
      008489                        970 00112$:
                                    971 ;	se8r01-receive-pwm.c: 360: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_IF_FREQ, temp, 3);
      008489 1E 06            [ 2]  972 	ldw	x, (0x06, sp)
      00848B 4B 03            [ 1]  973 	push	#0x03
      00848D 89               [ 2]  974 	pushw	x
      00848E 4B 2A            [ 1]  975 	push	#0x2a
      008490 CD 81 48         [ 4]  976 	call	_write_spi_buf
      008493 5B 04            [ 2]  977 	addw	sp, #4
                                    978 ;	se8r01-receive-pwm.c: 362: if (SE8R01_DR_2M==1)
      008495 CE 00 10         [ 2]  979 	ldw	x, _SE8R01_DR_2M+0
      008498 A3 00 01         [ 2]  980 	cpw	x, #0x0001
      00849B 26 07            [ 1]  981 	jrne	00114$
                                    982 ;	se8r01-receive-pwm.c: 363: { temp[0]=0x29;}
      00849D 1E 06            [ 2]  983 	ldw	x, (0x06, sp)
      00849F A6 29            [ 1]  984 	ld	a, #0x29
      0084A1 F7               [ 1]  985 	ld	(x), a
      0084A2 20 05            [ 2]  986 	jra	00115$
      0084A4                        987 00114$:
                                    988 ;	se8r01-receive-pwm.c: 365: { temp[0]=0x14;}
      0084A4 1E 06            [ 2]  989 	ldw	x, (0x06, sp)
      0084A6 A6 14            [ 1]  990 	ld	a, #0x14
      0084A8 F7               [ 1]  991 	ld	(x), a
      0084A9                        992 00115$:
                                    993 ;	se8r01-receive-pwm.c: 367: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FDEV, temp, 1);
      0084A9 1E 06            [ 2]  994 	ldw	x, (0x06, sp)
      0084AB 4B 01            [ 1]  995 	push	#0x01
      0084AD 89               [ 2]  996 	pushw	x
      0084AE 4B 2C            [ 1]  997 	push	#0x2c
      0084B0 CD 81 48         [ 4]  998 	call	_write_spi_buf
      0084B3 5B 04            [ 2]  999 	addw	sp, #4
                                   1000 ;	se8r01-receive-pwm.c: 369: temp[0]=0x00;
      0084B5 1E 06            [ 2] 1001 	ldw	x, (0x06, sp)
      0084B7 7F               [ 1] 1002 	clr	(x)
                                   1003 ;	se8r01-receive-pwm.c: 370: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_DAC_CAL_LOW,temp,1);
      0084B8 1E 06            [ 2] 1004 	ldw	x, (0x06, sp)
      0084BA 4B 01            [ 1] 1005 	push	#0x01
      0084BC 89               [ 2] 1006 	pushw	x
      0084BD 4B 37            [ 1] 1007 	push	#0x37
      0084BF CD 81 48         [ 4] 1008 	call	_write_spi_buf
      0084C2 5B 04            [ 2] 1009 	addw	sp, #4
                                   1010 ;	se8r01-receive-pwm.c: 372: temp[0]=0x7F;
      0084C4 1E 06            [ 2] 1011 	ldw	x, (0x06, sp)
      0084C6 A6 7F            [ 1] 1012 	ld	a, #0x7f
      0084C8 F7               [ 1] 1013 	ld	(x), a
                                   1014 ;	se8r01-receive-pwm.c: 373: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_DAC_CAL_HI,temp,1);
      0084C9 1E 06            [ 2] 1015 	ldw	x, (0x06, sp)
      0084CB 4B 01            [ 1] 1016 	push	#0x01
      0084CD 89               [ 2] 1017 	pushw	x
      0084CE 4B 38            [ 1] 1018 	push	#0x38
      0084D0 CD 81 48         [ 4] 1019 	call	_write_spi_buf
      0084D3 5B 04            [ 2] 1020 	addw	sp, #4
                                   1021 ;	se8r01-receive-pwm.c: 375: temp[0]=0x02;
      0084D5 1E 06            [ 2] 1022 	ldw	x, (0x06, sp)
      0084D7 A6 02            [ 1] 1023 	ld	a, #0x02
      0084D9 F7               [ 1] 1024 	ld	(x), a
                                   1025 ;	se8r01-receive-pwm.c: 376: temp[1]=0xC1;
      0084DA 1E 0C            [ 2] 1026 	ldw	x, (0x0c, sp)
      0084DC A6 C1            [ 1] 1027 	ld	a, #0xc1
      0084DE F7               [ 1] 1028 	ld	(x), a
                                   1029 ;	se8r01-receive-pwm.c: 377: temp[2]=0xEB;            
      0084DF 1E 0A            [ 2] 1030 	ldw	x, (0x0a, sp)
      0084E1 A6 EB            [ 1] 1031 	ld	a, #0xeb
      0084E3 F7               [ 1] 1032 	ld	(x), a
                                   1033 ;	se8r01-receive-pwm.c: 378: temp[3]=0x1C;
      0084E4 1E 08            [ 2] 1034 	ldw	x, (0x08, sp)
      0084E6 A6 1C            [ 1] 1035 	ld	a, #0x1c
      0084E8 F7               [ 1] 1036 	ld	(x), a
                                   1037 ;	se8r01-receive-pwm.c: 379: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_AGC_GAIN, temp,4);
      0084E9 1E 06            [ 2] 1038 	ldw	x, (0x06, sp)
      0084EB 4B 04            [ 1] 1039 	push	#0x04
      0084ED 89               [ 2] 1040 	pushw	x
      0084EE 4B 3D            [ 1] 1041 	push	#0x3d
      0084F0 CD 81 48         [ 4] 1042 	call	_write_spi_buf
      0084F3 5B 04            [ 2] 1043 	addw	sp, #4
                                   1044 ;	se8r01-receive-pwm.c: 381: temp[0]=0x97;
      0084F5 1E 06            [ 2] 1045 	ldw	x, (0x06, sp)
      0084F7 A6 97            [ 1] 1046 	ld	a, #0x97
      0084F9 F7               [ 1] 1047 	ld	(x), a
                                   1048 ;	se8r01-receive-pwm.c: 382: temp[1]=0x64;
      0084FA 1E 0C            [ 2] 1049 	ldw	x, (0x0c, sp)
      0084FC A6 64            [ 1] 1050 	ld	a, #0x64
      0084FE F7               [ 1] 1051 	ld	(x), a
                                   1052 ;	se8r01-receive-pwm.c: 383: temp[2]=0x00;
      0084FF 1E 0A            [ 2] 1053 	ldw	x, (0x0a, sp)
      008501 7F               [ 1] 1054 	clr	(x)
                                   1055 ;	se8r01-receive-pwm.c: 384: temp[3]=0x81;
      008502 1E 08            [ 2] 1056 	ldw	x, (0x08, sp)
      008504 A6 81            [ 1] 1057 	ld	a, #0x81
      008506 F7               [ 1] 1058 	ld	(x), a
                                   1059 ;	se8r01-receive-pwm.c: 385: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RF_IVGEN, temp, 4);
      008507 1E 06            [ 2] 1060 	ldw	x, (0x06, sp)
      008509 4B 04            [ 1] 1061 	push	#0x04
      00850B 89               [ 2] 1062 	pushw	x
      00850C 4B 3E            [ 1] 1063 	push	#0x3e
      00850E CD 81 48         [ 4] 1064 	call	_write_spi_buf
      008511 5B 04            [ 2] 1065 	addw	sp, #4
                                   1066 ;	se8r01-receive-pwm.c: 386: rf_switch_bank(iBANK0);
      008513 4B 00            [ 1] 1067 	push	#0x00
      008515 CD 83 79         [ 4] 1068 	call	_rf_switch_bank
      008518 84               [ 1] 1069 	pop	a
                                   1070 ;	se8r01-receive-pwm.c: 391: delayTenMicro();
      008519 CD 80 A0         [ 4] 1071 	call	_delayTenMicro
                                   1072 ;	se8r01-receive-pwm.c: 392: PC_ODR |= (1 << CE);
      00851C AE 50 0A         [ 2] 1073 	ldw	x, #0x500a
      00851F F6               [ 1] 1074 	ld	a, (x)
      008520 AA 10            [ 1] 1075 	or	a, #0x10
      008522 F7               [ 1] 1076 	ld	(x), a
                                   1077 ;	se8r01-receive-pwm.c: 393: delayTenMicro();
      008523 CD 80 A0         [ 4] 1078 	call	_delayTenMicro
                                   1079 ;	se8r01-receive-pwm.c: 394: delayTenMicro();
      008526 CD 80 A0         [ 4] 1080 	call	_delayTenMicro
                                   1081 ;	se8r01-receive-pwm.c: 395: delayTenMicro();
      008529 CD 80 A0         [ 4] 1082 	call	_delayTenMicro
                                   1083 ;	se8r01-receive-pwm.c: 396: PC_ODR &= ~(1 << CE);
      00852C AE 50 0A         [ 2] 1084 	ldw	x, #0x500a
      00852F F6               [ 1] 1085 	ld	a, (x)
      008530 A4 EF            [ 1] 1086 	and	a, #0xef
      008532 F7               [ 1] 1087 	ld	(x), a
                                   1088 ;	se8r01-receive-pwm.c: 397: delay(50);                            // delay 50ms waitting for calibaration.
      008533 4B 32            [ 1] 1089 	push	#0x32
      008535 4B 00            [ 1] 1090 	push	#0x00
      008537 CD 82 2E         [ 4] 1091 	call	_delay
      00853A 5B 02            [ 2] 1092 	addw	sp, #2
                                   1093 ;	se8r01-receive-pwm.c: 402: delayTenMicro();
      00853C CD 80 A0         [ 4] 1094 	call	_delayTenMicro
                                   1095 ;	se8r01-receive-pwm.c: 403: PC_ODR |= (1 << CE);
      00853F AE 50 0A         [ 2] 1096 	ldw	x, #0x500a
      008542 F6               [ 1] 1097 	ld	a, (x)
      008543 AA 10            [ 1] 1098 	or	a, #0x10
      008545 F7               [ 1] 1099 	ld	(x), a
                                   1100 ;	se8r01-receive-pwm.c: 404: delayTenMicro();
      008546 CD 80 A0         [ 4] 1101 	call	_delayTenMicro
                                   1102 ;	se8r01-receive-pwm.c: 405: delayTenMicro();
      008549 CD 80 A0         [ 4] 1103 	call	_delayTenMicro
                                   1104 ;	se8r01-receive-pwm.c: 406: delayTenMicro();
      00854C CD 80 A0         [ 4] 1105 	call	_delayTenMicro
                                   1106 ;	se8r01-receive-pwm.c: 407: PC_ODR &= ~(1 << CE);
      00854F AE 50 0A         [ 2] 1107 	ldw	x, #0x500a
      008552 F6               [ 1] 1108 	ld	a, (x)
      008553 A4 EF            [ 1] 1109 	and	a, #0xef
      008555 F7               [ 1] 1110 	ld	(x), a
                                   1111 ;	se8r01-receive-pwm.c: 408: delay(50);                            // delay 50ms waitting for calibaration.
      008556 4B 32            [ 1] 1112 	push	#0x32
      008558 4B 00            [ 1] 1113 	push	#0x00
      00855A CD 82 2E         [ 4] 1114 	call	_delay
      00855D 5B 02            [ 2] 1115 	addw	sp, #2
      00855F 5B 0D            [ 2] 1116 	addw	sp, #13
      008561 81               [ 4] 1117 	ret
                                   1118 ;	se8r01-receive-pwm.c: 412: void SE8R01_Analog_Init()           //SE8R01 初始化
                                   1119 ;	-----------------------------------------
                                   1120 ;	 function SE8R01_Analog_Init
                                   1121 ;	-----------------------------------------
      008562                       1122 _SE8R01_Analog_Init:
      008562 52 15            [ 2] 1123 	sub	sp, #21
                                   1124 ;	se8r01-receive-pwm.c: 417: gtemp[0]=0x28;
      008564 AE 00 01         [ 2] 1125 	ldw	x, #_gtemp+0
      008567 1F 14            [ 2] 1126 	ldw	(0x14, sp), x
      008569 1E 14            [ 2] 1127 	ldw	x, (0x14, sp)
      00856B A6 28            [ 1] 1128 	ld	a, #0x28
      00856D F7               [ 1] 1129 	ld	(x), a
                                   1130 ;	se8r01-receive-pwm.c: 418: gtemp[1]=0x32;
      00856E 1E 14            [ 2] 1131 	ldw	x, (0x14, sp)
      008570 5C               [ 2] 1132 	incw	x
      008571 1F 08            [ 2] 1133 	ldw	(0x08, sp), x
      008573 1E 08            [ 2] 1134 	ldw	x, (0x08, sp)
      008575 A6 32            [ 1] 1135 	ld	a, #0x32
      008577 F7               [ 1] 1136 	ld	(x), a
                                   1137 ;	se8r01-receive-pwm.c: 419: gtemp[2]=0x80;
      008578 1E 14            [ 2] 1138 	ldw	x, (0x14, sp)
      00857A 5C               [ 2] 1139 	incw	x
      00857B 5C               [ 2] 1140 	incw	x
      00857C 1F 06            [ 2] 1141 	ldw	(0x06, sp), x
      00857E 1E 06            [ 2] 1142 	ldw	x, (0x06, sp)
      008580 A6 80            [ 1] 1143 	ld	a, #0x80
      008582 F7               [ 1] 1144 	ld	(x), a
                                   1145 ;	se8r01-receive-pwm.c: 420: gtemp[3]=0x90;
      008583 1E 14            [ 2] 1146 	ldw	x, (0x14, sp)
      008585 1C 00 03         [ 2] 1147 	addw	x, #0x0003
      008588 1F 0E            [ 2] 1148 	ldw	(0x0e, sp), x
      00858A 1E 0E            [ 2] 1149 	ldw	x, (0x0e, sp)
      00858C A6 90            [ 1] 1150 	ld	a, #0x90
      00858E F7               [ 1] 1151 	ld	(x), a
                                   1152 ;	se8r01-receive-pwm.c: 421: gtemp[4]=0x00;
      00858F 1E 14            [ 2] 1153 	ldw	x, (0x14, sp)
      008591 1C 00 04         [ 2] 1154 	addw	x, #0x0004
      008594 7F               [ 1] 1155 	clr	(x)
                                   1156 ;	se8r01-receive-pwm.c: 422: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_SETUP_VALUE, gtemp, 5);
      008595 1E 14            [ 2] 1157 	ldw	x, (0x14, sp)
      008597 4B 05            [ 1] 1158 	push	#0x05
      008599 89               [ 2] 1159 	pushw	x
      00859A 4B 3E            [ 1] 1160 	push	#0x3e
      00859C CD 81 48         [ 4] 1161 	call	_write_spi_buf
      00859F 5B 04            [ 2] 1162 	addw	sp, #4
                                   1163 ;	se8r01-receive-pwm.c: 423: delay(2);
      0085A1 4B 02            [ 1] 1164 	push	#0x02
      0085A3 4B 00            [ 1] 1165 	push	#0x00
      0085A5 CD 82 2E         [ 4] 1166 	call	_delay
      0085A8 5B 02            [ 2] 1167 	addw	sp, #2
                                   1168 ;	se8r01-receive-pwm.c: 426: rf_switch_bank(iBANK1);
      0085AA 4B 80            [ 1] 1169 	push	#0x80
      0085AC CD 83 79         [ 4] 1170 	call	_rf_switch_bank
      0085AF 84               [ 1] 1171 	pop	a
                                   1172 ;	se8r01-receive-pwm.c: 428: temp[0]=0x40;
      0085B0 96               [ 1] 1173 	ldw	x, sp
      0085B1 5C               [ 2] 1174 	incw	x
      0085B2 1F 0C            [ 2] 1175 	ldw	(0x0c, sp), x
      0085B4 1E 0C            [ 2] 1176 	ldw	x, (0x0c, sp)
      0085B6 A6 40            [ 1] 1177 	ld	a, #0x40
      0085B8 F7               [ 1] 1178 	ld	(x), a
                                   1179 ;	se8r01-receive-pwm.c: 429: temp[1]=0x01;               
      0085B9 1E 0C            [ 2] 1180 	ldw	x, (0x0c, sp)
      0085BB 5C               [ 2] 1181 	incw	x
      0085BC 1F 0A            [ 2] 1182 	ldw	(0x0a, sp), x
      0085BE 1E 0A            [ 2] 1183 	ldw	x, (0x0a, sp)
      0085C0 A6 01            [ 1] 1184 	ld	a, #0x01
      0085C2 F7               [ 1] 1185 	ld	(x), a
                                   1186 ;	se8r01-receive-pwm.c: 430: temp[2]=0x30;               
      0085C3 1E 0C            [ 2] 1187 	ldw	x, (0x0c, sp)
      0085C5 5C               [ 2] 1188 	incw	x
      0085C6 5C               [ 2] 1189 	incw	x
      0085C7 1F 12            [ 2] 1190 	ldw	(0x12, sp), x
      0085C9 1E 12            [ 2] 1191 	ldw	x, (0x12, sp)
      0085CB A6 30            [ 1] 1192 	ld	a, #0x30
      0085CD F7               [ 1] 1193 	ld	(x), a
                                   1194 ;	se8r01-receive-pwm.c: 432: { temp[3]=0xE2; }              
      0085CE 1E 0C            [ 2] 1195 	ldw	x, (0x0c, sp)
      0085D0 1C 00 03         [ 2] 1196 	addw	x, #0x0003
      0085D3 1F 10            [ 2] 1197 	ldw	(0x10, sp), x
                                   1198 ;	se8r01-receive-pwm.c: 431: if (SE8R01_DR_2M==1)
      0085D5 CE 00 10         [ 2] 1199 	ldw	x, _SE8R01_DR_2M+0
      0085D8 A3 00 01         [ 2] 1200 	cpw	x, #0x0001
      0085DB 26 07            [ 1] 1201 	jrne	00102$
                                   1202 ;	se8r01-receive-pwm.c: 432: { temp[3]=0xE2; }              
      0085DD 1E 10            [ 2] 1203 	ldw	x, (0x10, sp)
      0085DF A6 E2            [ 1] 1204 	ld	a, #0xe2
      0085E1 F7               [ 1] 1205 	ld	(x), a
      0085E2 20 05            [ 2] 1206 	jra	00103$
      0085E4                       1207 00102$:
                                   1208 ;	se8r01-receive-pwm.c: 434: { temp[3]=0xE0;}
      0085E4 1E 10            [ 2] 1209 	ldw	x, (0x10, sp)
      0085E6 A6 E0            [ 1] 1210 	ld	a, #0xe0
      0085E8 F7               [ 1] 1211 	ld	(x), a
      0085E9                       1212 00103$:
                                   1213 ;	se8r01-receive-pwm.c: 436: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_PLL_CTL0, temp,4);
      0085E9 1E 0C            [ 2] 1214 	ldw	x, (0x0c, sp)
      0085EB 4B 04            [ 1] 1215 	push	#0x04
      0085ED 89               [ 2] 1216 	pushw	x
      0085EE 4B 21            [ 1] 1217 	push	#0x21
      0085F0 CD 81 48         [ 4] 1218 	call	_write_spi_buf
      0085F3 5B 04            [ 2] 1219 	addw	sp, #4
                                   1220 ;	se8r01-receive-pwm.c: 438: temp[0]=0x29;
      0085F5 1E 0C            [ 2] 1221 	ldw	x, (0x0c, sp)
      0085F7 A6 29            [ 1] 1222 	ld	a, #0x29
      0085F9 F7               [ 1] 1223 	ld	(x), a
                                   1224 ;	se8r01-receive-pwm.c: 439: temp[1]=0x89;
      0085FA 1E 0A            [ 2] 1225 	ldw	x, (0x0a, sp)
      0085FC A6 89            [ 1] 1226 	ld	a, #0x89
      0085FE F7               [ 1] 1227 	ld	(x), a
                                   1228 ;	se8r01-receive-pwm.c: 440: temp[2]=0x55;                     
      0085FF 1E 12            [ 2] 1229 	ldw	x, (0x12, sp)
      008601 A6 55            [ 1] 1230 	ld	a, #0x55
      008603 F7               [ 1] 1231 	ld	(x), a
                                   1232 ;	se8r01-receive-pwm.c: 441: temp[3]=0x40;
      008604 1E 10            [ 2] 1233 	ldw	x, (0x10, sp)
      008606 A6 40            [ 1] 1234 	ld	a, #0x40
      008608 F7               [ 1] 1235 	ld	(x), a
                                   1236 ;	se8r01-receive-pwm.c: 442: temp[4]=0x50;
      008609 1E 0C            [ 2] 1237 	ldw	x, (0x0c, sp)
      00860B A6 50            [ 1] 1238 	ld	a, #0x50
      00860D E7 04            [ 1] 1239 	ld	(0x0004, x), a
                                   1240 ;	se8r01-receive-pwm.c: 443: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_CAL_CTL, temp,5);
      00860F 1E 0C            [ 2] 1241 	ldw	x, (0x0c, sp)
      008611 4B 05            [ 1] 1242 	push	#0x05
      008613 89               [ 2] 1243 	pushw	x
      008614 4B 23            [ 1] 1244 	push	#0x23
      008616 CD 81 48         [ 4] 1245 	call	_write_spi_buf
      008619 5B 04            [ 2] 1246 	addw	sp, #4
                                   1247 ;	se8r01-receive-pwm.c: 445: if (SE8R01_DR_2M==1)
      00861B CE 00 10         [ 2] 1248 	ldw	x, _SE8R01_DR_2M+0
      00861E A3 00 01         [ 2] 1249 	cpw	x, #0x0001
      008621 26 07            [ 1] 1250 	jrne	00105$
                                   1251 ;	se8r01-receive-pwm.c: 446: { temp[0]=0x29;}
      008623 1E 0C            [ 2] 1252 	ldw	x, (0x0c, sp)
      008625 A6 29            [ 1] 1253 	ld	a, #0x29
      008627 F7               [ 1] 1254 	ld	(x), a
      008628 20 05            [ 2] 1255 	jra	00106$
      00862A                       1256 00105$:
                                   1257 ;	se8r01-receive-pwm.c: 448: { temp[0]=0x14;}
      00862A 1E 0C            [ 2] 1258 	ldw	x, (0x0c, sp)
      00862C A6 14            [ 1] 1259 	ld	a, #0x14
      00862E F7               [ 1] 1260 	ld	(x), a
      00862F                       1261 00106$:
                                   1262 ;	se8r01-receive-pwm.c: 450: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FDEV, temp,1);
      00862F 1E 0C            [ 2] 1263 	ldw	x, (0x0c, sp)
      008631 4B 01            [ 1] 1264 	push	#0x01
      008633 89               [ 2] 1265 	pushw	x
      008634 4B 2C            [ 1] 1266 	push	#0x2c
      008636 CD 81 48         [ 4] 1267 	call	_write_spi_buf
      008639 5B 04            [ 2] 1268 	addw	sp, #4
                                   1269 ;	se8r01-receive-pwm.c: 452: temp[0]=0x55;
      00863B 1E 0C            [ 2] 1270 	ldw	x, (0x0c, sp)
      00863D A6 55            [ 1] 1271 	ld	a, #0x55
      00863F F7               [ 1] 1272 	ld	(x), a
                                   1273 ;	se8r01-receive-pwm.c: 453: temp[1]=0xC2;
      008640 1E 0A            [ 2] 1274 	ldw	x, (0x0a, sp)
      008642 A6 C2            [ 1] 1275 	ld	a, #0xc2
      008644 F7               [ 1] 1276 	ld	(x), a
                                   1277 ;	se8r01-receive-pwm.c: 454: temp[2]=0x09;
      008645 1E 12            [ 2] 1278 	ldw	x, (0x12, sp)
      008647 A6 09            [ 1] 1279 	ld	a, #0x09
      008649 F7               [ 1] 1280 	ld	(x), a
                                   1281 ;	se8r01-receive-pwm.c: 455: temp[3]=0xAC;  
      00864A 1E 10            [ 2] 1282 	ldw	x, (0x10, sp)
      00864C A6 AC            [ 1] 1283 	ld	a, #0xac
      00864E F7               [ 1] 1284 	ld	(x), a
                                   1285 ;	se8r01-receive-pwm.c: 456: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RX_CTRL,temp,4);
      00864F 1E 0C            [ 2] 1286 	ldw	x, (0x0c, sp)
      008651 4B 04            [ 1] 1287 	push	#0x04
      008653 89               [ 2] 1288 	pushw	x
      008654 4B 31            [ 1] 1289 	push	#0x31
      008656 CD 81 48         [ 4] 1290 	call	_write_spi_buf
      008659 5B 04            [ 2] 1291 	addw	sp, #4
                                   1292 ;	se8r01-receive-pwm.c: 458: temp[0]=0x00;
      00865B 1E 0C            [ 2] 1293 	ldw	x, (0x0c, sp)
      00865D 7F               [ 1] 1294 	clr	(x)
                                   1295 ;	se8r01-receive-pwm.c: 459: temp[1]=0x14;
      00865E 1E 0A            [ 2] 1296 	ldw	x, (0x0a, sp)
      008660 A6 14            [ 1] 1297 	ld	a, #0x14
      008662 F7               [ 1] 1298 	ld	(x), a
                                   1299 ;	se8r01-receive-pwm.c: 460: temp[2]=0x08;   
      008663 1E 12            [ 2] 1300 	ldw	x, (0x12, sp)
      008665 A6 08            [ 1] 1301 	ld	a, #0x08
      008667 F7               [ 1] 1302 	ld	(x), a
                                   1303 ;	se8r01-receive-pwm.c: 461: temp[3]=0x29;
      008668 1E 10            [ 2] 1304 	ldw	x, (0x10, sp)
      00866A A6 29            [ 1] 1305 	ld	a, #0x29
      00866C F7               [ 1] 1306 	ld	(x), a
                                   1307 ;	se8r01-receive-pwm.c: 462: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FAGC_CTRL_1, temp,4);
      00866D 1E 0C            [ 2] 1308 	ldw	x, (0x0c, sp)
      00866F 4B 04            [ 1] 1309 	push	#0x04
      008671 89               [ 2] 1310 	pushw	x
      008672 4B 33            [ 1] 1311 	push	#0x33
      008674 CD 81 48         [ 4] 1312 	call	_write_spi_buf
      008677 5B 04            [ 2] 1313 	addw	sp, #4
                                   1314 ;	se8r01-receive-pwm.c: 464: temp[0]=0x02;
      008679 1E 0C            [ 2] 1315 	ldw	x, (0x0c, sp)
      00867B A6 02            [ 1] 1316 	ld	a, #0x02
      00867D F7               [ 1] 1317 	ld	(x), a
                                   1318 ;	se8r01-receive-pwm.c: 465: temp[1]=0xC1;
      00867E 1E 0A            [ 2] 1319 	ldw	x, (0x0a, sp)
      008680 A6 C1            [ 1] 1320 	ld	a, #0xc1
      008682 F7               [ 1] 1321 	ld	(x), a
                                   1322 ;	se8r01-receive-pwm.c: 466: temp[2]=0xCB;  
      008683 1E 12            [ 2] 1323 	ldw	x, (0x12, sp)
      008685 A6 CB            [ 1] 1324 	ld	a, #0xcb
      008687 F7               [ 1] 1325 	ld	(x), a
                                   1326 ;	se8r01-receive-pwm.c: 467: temp[3]=0x1C;
      008688 1E 10            [ 2] 1327 	ldw	x, (0x10, sp)
      00868A A6 1C            [ 1] 1328 	ld	a, #0x1c
      00868C F7               [ 1] 1329 	ld	(x), a
                                   1330 ;	se8r01-receive-pwm.c: 468: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_AGC_GAIN, temp,4);
      00868D 1E 0C            [ 2] 1331 	ldw	x, (0x0c, sp)
      00868F 4B 04            [ 1] 1332 	push	#0x04
      008691 89               [ 2] 1333 	pushw	x
      008692 4B 3D            [ 1] 1334 	push	#0x3d
      008694 CD 81 48         [ 4] 1335 	call	_write_spi_buf
      008697 5B 04            [ 2] 1336 	addw	sp, #4
                                   1337 ;	se8r01-receive-pwm.c: 470: temp[0]=0x97;
      008699 1E 0C            [ 2] 1338 	ldw	x, (0x0c, sp)
      00869B A6 97            [ 1] 1339 	ld	a, #0x97
      00869D F7               [ 1] 1340 	ld	(x), a
                                   1341 ;	se8r01-receive-pwm.c: 471: temp[1]=0x64;
      00869E 1E 0A            [ 2] 1342 	ldw	x, (0x0a, sp)
      0086A0 A6 64            [ 1] 1343 	ld	a, #0x64
      0086A2 F7               [ 1] 1344 	ld	(x), a
                                   1345 ;	se8r01-receive-pwm.c: 472: temp[2]=0x00;
      0086A3 1E 12            [ 2] 1346 	ldw	x, (0x12, sp)
      0086A5 7F               [ 1] 1347 	clr	(x)
                                   1348 ;	se8r01-receive-pwm.c: 473: temp[3]=0x01;
      0086A6 1E 10            [ 2] 1349 	ldw	x, (0x10, sp)
      0086A8 A6 01            [ 1] 1350 	ld	a, #0x01
      0086AA F7               [ 1] 1351 	ld	(x), a
                                   1352 ;	se8r01-receive-pwm.c: 474: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RF_IVGEN, temp,4);
      0086AB 1E 0C            [ 2] 1353 	ldw	x, (0x0c, sp)
      0086AD 4B 04            [ 1] 1354 	push	#0x04
      0086AF 89               [ 2] 1355 	pushw	x
      0086B0 4B 3E            [ 1] 1356 	push	#0x3e
      0086B2 CD 81 48         [ 4] 1357 	call	_write_spi_buf
      0086B5 5B 04            [ 2] 1358 	addw	sp, #4
                                   1359 ;	se8r01-receive-pwm.c: 476: gtemp[0]=0x2A;
      0086B7 1E 14            [ 2] 1360 	ldw	x, (0x14, sp)
      0086B9 A6 2A            [ 1] 1361 	ld	a, #0x2a
      0086BB F7               [ 1] 1362 	ld	(x), a
                                   1363 ;	se8r01-receive-pwm.c: 477: gtemp[1]=0x04;
      0086BC 1E 08            [ 2] 1364 	ldw	x, (0x08, sp)
      0086BE A6 04            [ 1] 1365 	ld	a, #0x04
      0086C0 F7               [ 1] 1366 	ld	(x), a
                                   1367 ;	se8r01-receive-pwm.c: 478: gtemp[2]=0x00;
      0086C1 1E 06            [ 2] 1368 	ldw	x, (0x06, sp)
      0086C3 7F               [ 1] 1369 	clr	(x)
                                   1370 ;	se8r01-receive-pwm.c: 479: gtemp[3]=0x7D;
      0086C4 1E 0E            [ 2] 1371 	ldw	x, (0x0e, sp)
      0086C6 A6 7D            [ 1] 1372 	ld	a, #0x7d
      0086C8 F7               [ 1] 1373 	ld	(x), a
                                   1374 ;	se8r01-receive-pwm.c: 480: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_TEST_PKDET, gtemp, 4);
      0086C9 1E 14            [ 2] 1375 	ldw	x, (0x14, sp)
      0086CB 4B 04            [ 1] 1376 	push	#0x04
      0086CD 89               [ 2] 1377 	pushw	x
      0086CE 4B 3F            [ 1] 1378 	push	#0x3f
      0086D0 CD 81 48         [ 4] 1379 	call	_write_spi_buf
      0086D3 5B 04            [ 2] 1380 	addw	sp, #4
                                   1381 ;	se8r01-receive-pwm.c: 482: rf_switch_bank(iBANK0);
      0086D5 4B 00            [ 1] 1382 	push	#0x00
      0086D7 CD 83 79         [ 4] 1383 	call	_rf_switch_bank
      0086DA 84               [ 1] 1384 	pop	a
      0086DB 5B 15            [ 2] 1385 	addw	sp, #21
      0086DD 81               [ 4] 1386 	ret
                                   1387 ;	se8r01-receive-pwm.c: 485: void SE8R01_Init()  
                                   1388 ;	-----------------------------------------
                                   1389 ;	 function SE8R01_Init
                                   1390 ;	-----------------------------------------
      0086DE                       1391 _SE8R01_Init:
      0086DE 52 05            [ 2] 1392 	sub	sp, #5
                                   1393 ;	se8r01-receive-pwm.c: 488: SE8R01_Calibration();   
      0086E0 CD 83 96         [ 4] 1394 	call	_SE8R01_Calibration
                                   1395 ;	se8r01-receive-pwm.c: 489: SE8R01_Analog_Init();   
      0086E3 CD 85 62         [ 4] 1396 	call	_SE8R01_Analog_Init
                                   1397 ;	se8r01-receive-pwm.c: 493: if (SE8R01_DR_2M==1)
      0086E6 CE 00 10         [ 2] 1398 	ldw	x, _SE8R01_DR_2M+0
      0086E9 A3 00 01         [ 2] 1399 	cpw	x, #0x0001
      0086EC 26 07            [ 1] 1400 	jrne	00105$
                                   1401 ;	se8r01-receive-pwm.c: 494: {  temp[0]=0b01001111; }     //2MHz,+5dbm
      0086EE 96               [ 1] 1402 	ldw	x, sp
      0086EF 5C               [ 2] 1403 	incw	x
      0086F0 A6 4F            [ 1] 1404 	ld	a, #0x4f
      0086F2 F7               [ 1] 1405 	ld	(x), a
      0086F3 20 14            [ 2] 1406 	jra	00106$
      0086F5                       1407 00105$:
                                   1408 ;	se8r01-receive-pwm.c: 495: else if  (SE8R01_DR_1M==1)
      0086F5 CE 00 12         [ 2] 1409 	ldw	x, _SE8R01_DR_1M+0
      0086F8 A3 00 01         [ 2] 1410 	cpw	x, #0x0001
      0086FB 26 07            [ 1] 1411 	jrne	00102$
                                   1412 ;	se8r01-receive-pwm.c: 496: {  temp[0]=0b01000111;  }     //1MHz,+5dbm
      0086FD 96               [ 1] 1413 	ldw	x, sp
      0086FE 5C               [ 2] 1414 	incw	x
      0086FF A6 47            [ 1] 1415 	ld	a, #0x47
      008701 F7               [ 1] 1416 	ld	(x), a
      008702 20 05            [ 2] 1417 	jra	00106$
      008704                       1418 00102$:
                                   1419 ;	se8r01-receive-pwm.c: 498: {temp[0]=0b01101111;  }     //500K,+5dbm
      008704 96               [ 1] 1420 	ldw	x, sp
      008705 5C               [ 2] 1421 	incw	x
      008706 A6 6F            [ 1] 1422 	ld	a, #0x6f
      008708 F7               [ 1] 1423 	ld	(x), a
      008709                       1424 00106$:
                                   1425 ;	se8r01-receive-pwm.c: 500: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_SETUP,temp,1);
      008709 96               [ 1] 1426 	ldw	x, sp
      00870A 5C               [ 2] 1427 	incw	x
      00870B 4B 01            [ 1] 1428 	push	#0x01
      00870D 89               [ 2] 1429 	pushw	x
      00870E 4B 26            [ 1] 1430 	push	#0x26
      008710 CD 81 48         [ 4] 1431 	call	_write_spi_buf
      008713 5B 04            [ 2] 1432 	addw	sp, #4
                                   1433 ;	se8r01-receive-pwm.c: 501: write_spi_reg(WRITE_REG|iRF_BANK0_EN_AA, 0b00111111);          //enable auto acc on pip 1
      008715 4B 3F            [ 1] 1434 	push	#0x3f
      008717 4B 21            [ 1] 1435 	push	#0x21
      008719 CD 80 CE         [ 4] 1436 	call	_write_spi_reg
      00871C 5B 02            [ 2] 1437 	addw	sp, #2
                                   1438 ;	se8r01-receive-pwm.c: 502: write_spi_reg(WRITE_REG|iRF_BANK0_EN_RXADDR, 0b00111111);      //enable pip 1
      00871E 4B 3F            [ 1] 1439 	push	#0x3f
      008720 4B 22            [ 1] 1440 	push	#0x22
      008722 CD 80 CE         [ 4] 1441 	call	_write_spi_reg
      008725 5B 02            [ 2] 1442 	addw	sp, #2
                                   1443 ;	se8r01-receive-pwm.c: 503: write_spi_reg(WRITE_REG|iRF_BANK0_SETUP_AW, 0x02);  
      008727 4B 02            [ 1] 1444 	push	#0x02
      008729 4B 23            [ 1] 1445 	push	#0x23
      00872B CD 80 CE         [ 4] 1446 	call	_write_spi_reg
      00872E 5B 02            [ 2] 1447 	addw	sp, #2
                                   1448 ;	se8r01-receive-pwm.c: 504: write_spi_reg(WRITE_REG|iRF_BANK0_RF_CH, 40);
      008730 4B 28            [ 1] 1449 	push	#0x28
      008732 4B 25            [ 1] 1450 	push	#0x25
      008734 CD 80 CE         [ 4] 1451 	call	_write_spi_reg
      008737 5B 02            [ 2] 1452 	addw	sp, #2
                                   1453 ;	se8r01-receive-pwm.c: 506: write_spi_buf(WRITE_REG + TX_ADDR, ADDRESS0, ADR_WIDTH);    	
      008739 AE 00 2A         [ 2] 1454 	ldw	x, #_ADDRESS0+0
      00873C 90 93            [ 1] 1455 	ldw	y, x
      00873E 89               [ 2] 1456 	pushw	x
      00873F 4B 04            [ 1] 1457 	push	#0x04
      008741 90 89            [ 2] 1458 	pushw	y
      008743 4B 30            [ 1] 1459 	push	#0x30
      008745 CD 81 48         [ 4] 1460 	call	_write_spi_buf
      008748 5B 04            [ 2] 1461 	addw	sp, #4
      00874A 85               [ 2] 1462 	popw	x
                                   1463 ;	se8r01-receive-pwm.c: 507: write_spi_buf(WRITE_REG + RX_ADDR_P0, ADDRESS0, ADR_WIDTH); 
      00874B 4B 04            [ 1] 1464 	push	#0x04
      00874D 89               [ 2] 1465 	pushw	x
      00874E 4B 2A            [ 1] 1466 	push	#0x2a
      008750 CD 81 48         [ 4] 1467 	call	_write_spi_buf
      008753 5B 04            [ 2] 1468 	addw	sp, #4
                                   1469 ;	se8r01-receive-pwm.c: 508: write_spi_buf(WRITE_REG + RX_ADDR_P1, ADDRESS1, ADR_WIDTH); 
      008755 AE 00 26         [ 2] 1470 	ldw	x, #_ADDRESS1+0
      008758 4B 04            [ 1] 1471 	push	#0x04
      00875A 89               [ 2] 1472 	pushw	x
      00875B 4B 2B            [ 1] 1473 	push	#0x2b
      00875D CD 81 48         [ 4] 1474 	call	_write_spi_buf
      008760 5B 04            [ 2] 1475 	addw	sp, #4
                                   1476 ;	se8r01-receive-pwm.c: 509: write_spi_buf(WRITE_REG + RX_ADDR_P2, ADDRESS2, 1); 
      008762 AE 00 22         [ 2] 1477 	ldw	x, #_ADDRESS2+0
      008765 4B 01            [ 1] 1478 	push	#0x01
      008767 89               [ 2] 1479 	pushw	x
      008768 4B 2C            [ 1] 1480 	push	#0x2c
      00876A CD 81 48         [ 4] 1481 	call	_write_spi_buf
      00876D 5B 04            [ 2] 1482 	addw	sp, #4
                                   1483 ;	se8r01-receive-pwm.c: 510: write_spi_buf(WRITE_REG + RX_ADDR_P3, ADDRESS3, 1); 
      00876F AE 00 23         [ 2] 1484 	ldw	x, #_ADDRESS3+0
      008772 4B 01            [ 1] 1485 	push	#0x01
      008774 89               [ 2] 1486 	pushw	x
      008775 4B 2D            [ 1] 1487 	push	#0x2d
      008777 CD 81 48         [ 4] 1488 	call	_write_spi_buf
      00877A 5B 04            [ 2] 1489 	addw	sp, #4
                                   1490 ;	se8r01-receive-pwm.c: 511: write_spi_buf(WRITE_REG + RX_ADDR_P4, ADDRESS4, 1); 
      00877C AE 00 24         [ 2] 1491 	ldw	x, #_ADDRESS4+0
      00877F 4B 01            [ 1] 1492 	push	#0x01
      008781 89               [ 2] 1493 	pushw	x
      008782 4B 2E            [ 1] 1494 	push	#0x2e
      008784 CD 81 48         [ 4] 1495 	call	_write_spi_buf
      008787 5B 04            [ 2] 1496 	addw	sp, #4
                                   1497 ;	se8r01-receive-pwm.c: 512: write_spi_buf(WRITE_REG + RX_ADDR_P5, ADDRESS5, 1); 
      008789 AE 00 25         [ 2] 1498 	ldw	x, #_ADDRESS5+0
      00878C 4B 01            [ 1] 1499 	push	#0x01
      00878E 89               [ 2] 1500 	pushw	x
      00878F 4B 2F            [ 1] 1501 	push	#0x2f
      008791 CD 81 48         [ 4] 1502 	call	_write_spi_buf
      008794 5B 04            [ 2] 1503 	addw	sp, #4
                                   1504 ;	se8r01-receive-pwm.c: 513: write_spi_reg(WRITE_REG + RX_PW_P0, PLOAD_WIDTH); 
      008796 4B 20            [ 1] 1505 	push	#0x20
      008798 4B 31            [ 1] 1506 	push	#0x31
      00879A CD 80 CE         [ 4] 1507 	call	_write_spi_reg
      00879D 5B 02            [ 2] 1508 	addw	sp, #2
                                   1509 ;	se8r01-receive-pwm.c: 514: write_spi_reg(WRITE_REG|iRF_BANK0_CONFIG, 0x3f); 
      00879F 4B 3F            [ 1] 1510 	push	#0x3f
      0087A1 4B 20            [ 1] 1511 	push	#0x20
      0087A3 CD 80 CE         [ 4] 1512 	call	_write_spi_reg
      0087A6 5B 02            [ 2] 1513 	addw	sp, #2
                                   1514 ;	se8r01-receive-pwm.c: 515: write_spi_reg(WRITE_REG|iRF_BANK0_DYNPD, 0b00111111);          // enable dynamic payload length data
      0087A8 4B 3F            [ 1] 1515 	push	#0x3f
      0087AA 4B 3C            [ 1] 1516 	push	#0x3c
      0087AC CD 80 CE         [ 4] 1517 	call	_write_spi_reg
      0087AF 5B 02            [ 2] 1518 	addw	sp, #2
                                   1519 ;	se8r01-receive-pwm.c: 516: write_spi_reg(WRITE_REG|iRF_BANK0_FEATURE, 0x07);        // enable dynamic paload lenght; enbale payload with ack enable w_tx_payload_noack
      0087B1 4B 07            [ 1] 1520 	push	#0x07
      0087B3 4B 3D            [ 1] 1521 	push	#0x3d
      0087B5 CD 80 CE         [ 4] 1522 	call	_write_spi_reg
      0087B8 5B 02            [ 2] 1523 	addw	sp, #2
                                   1524 ;	se8r01-receive-pwm.c: 517: PC_ODR |= (1 << CE);
      0087BA AE 50 0A         [ 2] 1525 	ldw	x, #0x500a
      0087BD F6               [ 1] 1526 	ld	a, (x)
      0087BE AA 10            [ 1] 1527 	or	a, #0x10
      0087C0 F7               [ 1] 1528 	ld	(x), a
      0087C1 5B 05            [ 2] 1529 	addw	sp, #5
      0087C3 81               [ 4] 1530 	ret
                                   1531 ;	se8r01-receive-pwm.c: 523: int main () {
                                   1532 ;	-----------------------------------------
                                   1533 ;	 function main
                                   1534 ;	-----------------------------------------
      0087C4                       1535 _main:
      0087C4 52 33            [ 2] 1536 	sub	sp, #51
                                   1537 ;	se8r01-receive-pwm.c: 525: UCHAR rx_addr_p1[]  = { 0xd2, 0xf0, 0xf0, 0xf0, 0xf0 };
      0087C6 90 96            [ 1] 1538 	ldw	y, sp
      0087C8 72 A9 00 0C      [ 2] 1539 	addw	y, #12
      0087CC A6 D2            [ 1] 1540 	ld	a, #0xd2
      0087CE 90 F7            [ 1] 1541 	ld	(y), a
      0087D0 93               [ 1] 1542 	ldw	x, y
      0087D1 5C               [ 2] 1543 	incw	x
      0087D2 A6 F0            [ 1] 1544 	ld	a, #0xf0
      0087D4 F7               [ 1] 1545 	ld	(x), a
      0087D5 93               [ 1] 1546 	ldw	x, y
      0087D6 5C               [ 2] 1547 	incw	x
      0087D7 5C               [ 2] 1548 	incw	x
      0087D8 A6 F0            [ 1] 1549 	ld	a, #0xf0
      0087DA F7               [ 1] 1550 	ld	(x), a
      0087DB 93               [ 1] 1551 	ldw	x, y
      0087DC A6 F0            [ 1] 1552 	ld	a, #0xf0
      0087DE E7 03            [ 1] 1553 	ld	(0x0003, x), a
      0087E0 93               [ 1] 1554 	ldw	x, y
      0087E1 A6 F0            [ 1] 1555 	ld	a, #0xf0
      0087E3 E7 04            [ 1] 1556 	ld	(0x0004, x), a
                                   1557 ;	se8r01-receive-pwm.c: 526: UCHAR tx_addr[]     = { 0xe1, 0xf0, 0xf0, 0xf0, 0xf0 };
      0087E5 90 96            [ 1] 1558 	ldw	y, sp
      0087E7 72 A9 00 07      [ 2] 1559 	addw	y, #7
      0087EB A6 E1            [ 1] 1560 	ld	a, #0xe1
      0087ED 90 F7            [ 1] 1561 	ld	(y), a
      0087EF 93               [ 1] 1562 	ldw	x, y
      0087F0 5C               [ 2] 1563 	incw	x
      0087F1 A6 F0            [ 1] 1564 	ld	a, #0xf0
      0087F3 F7               [ 1] 1565 	ld	(x), a
      0087F4 93               [ 1] 1566 	ldw	x, y
      0087F5 5C               [ 2] 1567 	incw	x
      0087F6 5C               [ 2] 1568 	incw	x
      0087F7 A6 F0            [ 1] 1569 	ld	a, #0xf0
      0087F9 F7               [ 1] 1570 	ld	(x), a
      0087FA 93               [ 1] 1571 	ldw	x, y
      0087FB A6 F0            [ 1] 1572 	ld	a, #0xf0
      0087FD E7 03            [ 1] 1573 	ld	(0x0003, x), a
      0087FF 93               [ 1] 1574 	ldw	x, y
      008800 1C 00 04         [ 2] 1575 	addw	x, #0x0004
      008803 A6 F0            [ 1] 1576 	ld	a, #0xf0
      008805 F7               [ 1] 1577 	ld	(x), a
                                   1578 ;	se8r01-receive-pwm.c: 531: InitializeSystemClock();
      008806 CD 81 E4         [ 4] 1579 	call	_InitializeSystemClock
                                   1580 ;	se8r01-receive-pwm.c: 532: InitializeUART();
      008809 CD 82 DC         [ 4] 1581 	call	_InitializeUART
                                   1582 ;	se8r01-receive-pwm.c: 534: InitializeSPI ();
      00880C CD 81 BC         [ 4] 1583 	call	_InitializeSPI
                                   1584 ;	se8r01-receive-pwm.c: 537: memset (tx_payload, 0, sizeof(tx_payload));
      00880F 96               [ 1] 1585 	ldw	x, sp
      008810 1C 00 11         [ 2] 1586 	addw	x, #17
      008813 4B 21            [ 1] 1587 	push	#0x21
      008815 4B 00            [ 1] 1588 	push	#0x00
      008817 4B 00            [ 1] 1589 	push	#0x00
      008819 4B 00            [ 1] 1590 	push	#0x00
      00881B 89               [ 2] 1591 	pushw	x
      00881C CD 89 99         [ 4] 1592 	call	_memset
      00881F 5B 06            [ 2] 1593 	addw	sp, #6
                                   1594 ;	se8r01-receive-pwm.c: 540: init_io();                        // Initialize IO port
      008821 CD 83 55         [ 4] 1595 	call	_init_io
                                   1596 ;	se8r01-receive-pwm.c: 541: write_spi_reg(FLUSH_RX,0); // receive data 
      008824 4B 00            [ 1] 1597 	push	#0x00
      008826 4B E2            [ 1] 1598 	push	#0xe2
      008828 CD 80 CE         [ 4] 1599 	call	_write_spi_reg
      00882B 5B 02            [ 2] 1600 	addw	sp, #2
                                   1601 ;	se8r01-receive-pwm.c: 542: readstatus = read_spi_reg(CONFIG);
      00882D 4B 00            [ 1] 1602 	push	#0x00
      00882F CD 81 0A         [ 4] 1603 	call	_read_spi_reg
      008832 5B 01            [ 2] 1604 	addw	sp, #1
                                   1605 ;	se8r01-receive-pwm.c: 543: UARTPrintF("config = \n\r");
      008834 AE 89 28         [ 2] 1606 	ldw	x, #___str_0+0
      008837 88               [ 1] 1607 	push	a
      008838 89               [ 2] 1608 	pushw	x
      008839 CD 82 79         [ 4] 1609 	call	_UARTPrintF
      00883C 5B 02            [ 2] 1610 	addw	sp, #2
      00883E 84               [ 1] 1611 	pop	a
                                   1612 ;	se8r01-receive-pwm.c: 544: print_UCHAR_hex(readstatus);
      00883F 88               [ 1] 1613 	push	a
      008840 CD 82 90         [ 4] 1614 	call	_print_UCHAR_hex
      008843 84               [ 1] 1615 	pop	a
                                   1616 ;	se8r01-receive-pwm.c: 545: readstatus = read_spi_reg(STATUS);
      008844 4B 07            [ 1] 1617 	push	#0x07
      008846 CD 81 0A         [ 4] 1618 	call	_read_spi_reg
      008849 5B 01            [ 2] 1619 	addw	sp, #1
                                   1620 ;	se8r01-receive-pwm.c: 546: UARTPrintF("status = \n\r");
      00884B AE 89 34         [ 2] 1621 	ldw	x, #___str_1+0
      00884E 88               [ 1] 1622 	push	a
      00884F 89               [ 2] 1623 	pushw	x
      008850 CD 82 79         [ 4] 1624 	call	_UARTPrintF
      008853 5B 02            [ 2] 1625 	addw	sp, #2
      008855 84               [ 1] 1626 	pop	a
                                   1627 ;	se8r01-receive-pwm.c: 547: print_UCHAR_hex(readstatus);
      008856 88               [ 1] 1628 	push	a
      008857 CD 82 90         [ 4] 1629 	call	_print_UCHAR_hex
      00885A 84               [ 1] 1630 	pop	a
                                   1631 ;	se8r01-receive-pwm.c: 549: SE8R01_Init();
      00885B CD 86 DE         [ 4] 1632 	call	_SE8R01_Init
                                   1633 ;	se8r01-receive-pwm.c: 553: while (1) {
      00885E                       1634 00110$:
                                   1635 ;	se8r01-receive-pwm.c: 555: if ((PD_IDR & (1 << 3))==0) //input low
      00885E AE 50 10         [ 2] 1636 	ldw	x, #0x5010
      008861 F6               [ 1] 1637 	ld	a, (x)
      008862 A5 08            [ 1] 1638 	bcp	a, #0x08
      008864 27 03            [ 1] 1639 	jreq	00170$
      008866 CC 88 EE         [ 2] 1640 	jp	00105$
      008869                       1641 00170$:
                                   1642 ;	se8r01-receive-pwm.c: 559: delay(240);
      008869 4B F0            [ 1] 1643 	push	#0xf0
      00886B 4B 00            [ 1] 1644 	push	#0x00
      00886D CD 82 2E         [ 4] 1645 	call	_delay
      008870 5B 02            [ 2] 1646 	addw	sp, #2
                                   1647 ;	se8r01-receive-pwm.c: 560: signal_lv=read_spi_reg(iRF_BANK0_RPD);
      008872 4B 09            [ 1] 1648 	push	#0x09
      008874 CD 81 0A         [ 4] 1649 	call	_read_spi_reg
      008877 5B 01            [ 2] 1650 	addw	sp, #1
      008879 C7 00 1A         [ 1] 1651 	ld	_signal_lv+0, a
                                   1652 ;	se8r01-receive-pwm.c: 561: status = read_spi_reg(STATUS);
      00887C 4B 07            [ 1] 1653 	push	#0x07
      00887E CD 81 0A         [ 4] 1654 	call	_read_spi_reg
      008881 5B 01            [ 2] 1655 	addw	sp, #1
      008883 C7 00 1D         [ 1] 1656 	ld	_status+0, a
                                   1657 ;	se8r01-receive-pwm.c: 563: if(status&STA_MARK_RX)                                                 // if receive data ready (TX_DS) interrupt
      008886 72 06 00 1D 02   [ 2] 1658 	btjt	_status+0, #6, 00171$
      00888B 20 57            [ 2] 1659 	jra	00103$
      00888D                       1660 00171$:
                                   1661 ;	se8r01-receive-pwm.c: 566: pip= (status & 0b00001110)>>1;
      00888D C6 00 1D         [ 1] 1662 	ld	a, _status+0
      008890 A4 0E            [ 1] 1663 	and	a, #0x0e
      008892 44               [ 1] 1664 	srl	a
      008893 5F               [ 1] 1665 	clrw	x
      008894 97               [ 1] 1666 	ld	xl, a
      008895 CF 00 1B         [ 2] 1667 	ldw	_pip+0, x
                                   1668 ;	se8r01-receive-pwm.c: 567: pload_width_now=read_spi_reg(iRF_CMD_R_RX_PL_WID);
      008898 4B 60            [ 1] 1669 	push	#0x60
      00889A CD 81 0A         [ 4] 1670 	call	_read_spi_reg
      00889D 5B 01            [ 2] 1671 	addw	sp, #1
      00889F 5F               [ 1] 1672 	clrw	x
      0088A0 97               [ 1] 1673 	ld	xl, a
      0088A1 CF 00 16         [ 2] 1674 	ldw	_pload_width_now+0, x
                                   1675 ;	se8r01-receive-pwm.c: 568: read_spi_buf(RD_RX_PLOAD, rx_buf,32);             // read playload to rx_buf
      0088A4 AE 00 2E         [ 2] 1676 	ldw	x, #_rx_buf+0
      0088A7 1F 32            [ 2] 1677 	ldw	(0x32, sp), x
      0088A9 1E 32            [ 2] 1678 	ldw	x, (0x32, sp)
      0088AB 4B 20            [ 1] 1679 	push	#0x20
      0088AD 89               [ 2] 1680 	pushw	x
      0088AE 4B 61            [ 1] 1681 	push	#0x61
      0088B0 CD 81 80         [ 4] 1682 	call	_read_spi_buf
      0088B3 5B 04            [ 2] 1683 	addw	sp, #4
                                   1684 ;	se8r01-receive-pwm.c: 569: write_spi_reg(FLUSH_RX,0);
      0088B5 4B 00            [ 1] 1685 	push	#0x00
      0088B7 4B E2            [ 1] 1686 	push	#0xe2
      0088B9 CD 80 CE         [ 4] 1687 	call	_write_spi_reg
      0088BC 5B 02            [ 2] 1688 	addw	sp, #2
                                   1689 ;	se8r01-receive-pwm.c: 571: newdata=1;
      0088BE 35 01 00 19      [ 1] 1690 	mov	_newdata+1, #0x01
      0088C2 72 5F 00 18      [ 1] 1691 	clr	_newdata+0
                                   1692 ;	se8r01-receive-pwm.c: 572: for (teller=0;teller<32;++teller)
      0088C6 5F               [ 1] 1693 	clrw	x
      0088C7                       1694 00112$:
                                   1695 ;	se8r01-receive-pwm.c: 573: print_UCHAR_hex (rx_buf[teller]);
      0088C7 90 93            [ 1] 1696 	ldw	y, x
      0088C9 72 F9 32         [ 2] 1697 	addw	y, (0x32, sp)
      0088CC 90 F6            [ 1] 1698 	ld	a, (y)
      0088CE 89               [ 2] 1699 	pushw	x
      0088CF 88               [ 1] 1700 	push	a
      0088D0 CD 82 90         [ 4] 1701 	call	_print_UCHAR_hex
      0088D3 84               [ 1] 1702 	pop	a
      0088D4 85               [ 2] 1703 	popw	x
                                   1704 ;	se8r01-receive-pwm.c: 572: for (teller=0;teller<32;++teller)
      0088D5 5C               [ 2] 1705 	incw	x
      0088D6 A3 00 20         [ 2] 1706 	cpw	x, #0x0020
      0088D9 2F EC            [ 1] 1707 	jrslt	00112$
                                   1708 ;	se8r01-receive-pwm.c: 574: UARTPrintF("\n\r");
      0088DB AE 89 40         [ 2] 1709 	ldw	x, #___str_2+0
      0088DE 89               [ 2] 1710 	pushw	x
      0088DF CD 82 79         [ 4] 1711 	call	_UARTPrintF
      0088E2 5B 02            [ 2] 1712 	addw	sp, #2
      0088E4                       1713 00103$:
                                   1714 ;	se8r01-receive-pwm.c: 577: write_spi_reg(WRITE_REG+STATUS,status);       // clear RX_DR or TX_DS or MAX_RT interrupt flag
      0088E4 3B 00 1D         [ 1] 1715 	push	_status+0
      0088E7 4B 27            [ 1] 1716 	push	#0x27
      0088E9 CD 80 CE         [ 4] 1717 	call	_write_spi_reg
      0088EC 5B 02            [ 2] 1718 	addw	sp, #2
      0088EE                       1719 00105$:
                                   1720 ;	se8r01-receive-pwm.c: 581: for (x1 = 0; x1 < 50; ++x1)
      0088EE 5F               [ 1] 1721 	clrw	x
      0088EF 1F 05            [ 2] 1722 	ldw	(0x05, sp), x
      0088F1                       1723 00121$:
      0088F1 1E 05            [ 2] 1724 	ldw	x, (0x05, sp)
      0088F3 A3 00 32         [ 2] 1725 	cpw	x, #0x0032
      0088F6 2F 03            [ 1] 1726 	jrslt	00173$
      0088F8 CC 88 5E         [ 2] 1727 	jp	00110$
      0088FB                       1728 00173$:
                                   1729 ;	se8r01-receive-pwm.c: 582: for (y1 = 0; y1 < 50; ++y1)
      0088FB 5F               [ 1] 1730 	clrw	x
      0088FC 1F 03            [ 2] 1731 	ldw	(0x03, sp), x
      0088FE                       1732 00118$:
      0088FE 1E 03            [ 2] 1733 	ldw	x, (0x03, sp)
      008900 A3 00 32         [ 2] 1734 	cpw	x, #0x0032
      008903 2E 19            [ 1] 1735 	jrsge	00122$
                                   1736 ;	se8r01-receive-pwm.c: 583: for (z1 = 0; z1 < 50; ++z1)
      008905 5F               [ 1] 1737 	clrw	x
      008906 1F 01            [ 2] 1738 	ldw	(0x01, sp), x
      008908                       1739 00115$:
      008908 1E 01            [ 2] 1740 	ldw	x, (0x01, sp)
      00890A A3 00 32         [ 2] 1741 	cpw	x, #0x0032
      00890D 2E 08            [ 1] 1742 	jrsge	00119$
                                   1743 ;	se8r01-receive-pwm.c: 584: __asm__("nop");
      00890F 9D               [ 1] 1744 	nop
                                   1745 ;	se8r01-receive-pwm.c: 583: for (z1 = 0; z1 < 50; ++z1)
      008910 1E 01            [ 2] 1746 	ldw	x, (0x01, sp)
      008912 5C               [ 2] 1747 	incw	x
      008913 1F 01            [ 2] 1748 	ldw	(0x01, sp), x
      008915 20 F1            [ 2] 1749 	jra	00115$
      008917                       1750 00119$:
                                   1751 ;	se8r01-receive-pwm.c: 582: for (y1 = 0; y1 < 50; ++y1)
      008917 1E 03            [ 2] 1752 	ldw	x, (0x03, sp)
      008919 5C               [ 2] 1753 	incw	x
      00891A 1F 03            [ 2] 1754 	ldw	(0x03, sp), x
      00891C 20 E0            [ 2] 1755 	jra	00118$
      00891E                       1756 00122$:
                                   1757 ;	se8r01-receive-pwm.c: 581: for (x1 = 0; x1 < 50; ++x1)
      00891E 1E 05            [ 2] 1758 	ldw	x, (0x05, sp)
      008920 5C               [ 2] 1759 	incw	x
      008921 1F 05            [ 2] 1760 	ldw	(0x05, sp), x
      008923 20 CC            [ 2] 1761 	jra	00121$
      008925 5B 33            [ 2] 1762 	addw	sp, #51
      008927 81               [ 4] 1763 	ret
                                   1764 	.area CODE
      008928                       1765 ___str_0:
      008928 63 6F 6E 66 69 67 20  1766 	.ascii "config = "
             3D 20
      008931 0A                    1767 	.db 0x0A
      008932 0D                    1768 	.db 0x0D
      008933 00                    1769 	.db 0x00
      008934                       1770 ___str_1:
      008934 73 74 61 74 75 73 20  1771 	.ascii "status = "
             3D 20
      00893D 0A                    1772 	.db 0x0A
      00893E 0D                    1773 	.db 0x0D
      00893F 00                    1774 	.db 0x00
      008940                       1775 ___str_2:
      008940 0A                    1776 	.db 0x0A
      008941 0D                    1777 	.db 0x0D
      008942 00                    1778 	.db 0x00
                                   1779 	.area INITIALIZER
      0089B8                       1780 __xinit__SE8R01_DR_2M:
      0089B8 00 00                 1781 	.dw #0x0000
      0089BA                       1782 __xinit__SE8R01_DR_1M:
      0089BA 00 00                 1783 	.dw #0x0000
      0089BC                       1784 __xinit__SE8R01_DR_500K:
      0089BC 00 01                 1785 	.dw #0x0001
      0089BE                       1786 __xinit__pload_width_now:
      0089BE 00 00                 1787 	.dw #0x0000
      0089C0                       1788 __xinit__newdata:
      0089C0 00 00                 1789 	.dw #0x0000
      0089C2                       1790 __xinit__signal_lv:
      0089C2 00                    1791 	.db #0x00	;  0
      0089C3                       1792 __xinit__pip:
      0089C3 00 00                 1793 	.dw #0x0000
      0089C5                       1794 __xinit__status:
      0089C5 00                    1795 	.db #0x00	; 0
      0089C6                       1796 __xinit__TX_ADDRESS:
      0089C6 B3                    1797 	.db #0xB3	; 179
      0089C7 43                    1798 	.db #0x43	; 67	'C'
      0089C8 10                    1799 	.db #0x10	; 16
      0089C9 10                    1800 	.db #0x10	; 16
      0089CA                       1801 __xinit__ADDRESS2:
      0089CA B1                    1802 	.db #0xB1	; 177
      0089CB                       1803 __xinit__ADDRESS3:
      0089CB B2                    1804 	.db #0xB2	; 178
      0089CC                       1805 __xinit__ADDRESS4:
      0089CC B3                    1806 	.db #0xB3	; 179
      0089CD                       1807 __xinit__ADDRESS5:
      0089CD B4                    1808 	.db #0xB4	; 180
      0089CE                       1809 __xinit__ADDRESS1:
      0089CE B0                    1810 	.db #0xB0	; 176
      0089CF 43                    1811 	.db #0x43	; 67	'C'
      0089D0 10                    1812 	.db #0x10	; 16
      0089D1 10                    1813 	.db #0x10	; 16
      0089D2                       1814 __xinit__ADDRESS0:
      0089D2 34                    1815 	.db #0x34	; 52	'4'
      0089D3 43                    1816 	.db #0x43	; 67	'C'
      0089D4 10                    1817 	.db #0x10	; 16
      0089D5 10                    1818 	.db #0x10	; 16
      0089D6                       1819 __xinit__rx_buf:
      0089D6 00                    1820 	.db #0x00	; 0
      0089D7 00                    1821 	.db 0x00
      0089D8 00                    1822 	.db 0x00
      0089D9 00                    1823 	.db 0x00
      0089DA 00                    1824 	.db 0x00
      0089DB 00                    1825 	.db 0x00
      0089DC 00                    1826 	.db 0x00
      0089DD 00                    1827 	.db 0x00
      0089DE 00                    1828 	.db 0x00
      0089DF 00                    1829 	.db 0x00
      0089E0 00                    1830 	.db 0x00
      0089E1 00                    1831 	.db 0x00
      0089E2 00                    1832 	.db 0x00
      0089E3 00                    1833 	.db 0x00
      0089E4 00                    1834 	.db 0x00
      0089E5 00                    1835 	.db 0x00
      0089E6 00                    1836 	.db 0x00
      0089E7 00                    1837 	.db 0x00
      0089E8 00                    1838 	.db 0x00
      0089E9 00                    1839 	.db 0x00
      0089EA 00                    1840 	.db 0x00
      0089EB 00                    1841 	.db 0x00
      0089EC 00                    1842 	.db 0x00
      0089ED 00                    1843 	.db 0x00
      0089EE 00                    1844 	.db 0x00
      0089EF 00                    1845 	.db 0x00
      0089F0 00                    1846 	.db 0x00
      0089F1 00                    1847 	.db 0x00
      0089F2 00                    1848 	.db 0x00
      0089F3 00                    1849 	.db 0x00
      0089F4 00                    1850 	.db 0x00
      0089F5 00                    1851 	.db 0x00
      0089F6                       1852 __xinit__tx_buf:
      0089F6 00                    1853 	.db #0x00	; 0
      0089F7 00                    1854 	.db 0x00
      0089F8 00                    1855 	.db 0x00
      0089F9 00                    1856 	.db 0x00
      0089FA 00                    1857 	.db 0x00
      0089FB 00                    1858 	.db 0x00
      0089FC 00                    1859 	.db 0x00
      0089FD 00                    1860 	.db 0x00
      0089FE 00                    1861 	.db 0x00
      0089FF 00                    1862 	.db 0x00
      008A00 00                    1863 	.db 0x00
      008A01 00                    1864 	.db 0x00
      008A02 00                    1865 	.db 0x00
      008A03 00                    1866 	.db 0x00
      008A04 00                    1867 	.db 0x00
      008A05 00                    1868 	.db 0x00
      008A06 00                    1869 	.db 0x00
      008A07 00                    1870 	.db 0x00
      008A08 00                    1871 	.db 0x00
      008A09 00                    1872 	.db 0x00
      008A0A 00                    1873 	.db 0x00
      008A0B 00                    1874 	.db 0x00
      008A0C 00                    1875 	.db 0x00
      008A0D 00                    1876 	.db 0x00
      008A0E 00                    1877 	.db 0x00
      008A0F 00                    1878 	.db 0x00
      008A10 00                    1879 	.db 0x00
      008A11 00                    1880 	.db 0x00
      008A12 00                    1881 	.db 0x00
      008A13 00                    1882 	.db 0x00
      008A14 00                    1883 	.db 0x00
      008A15 00                    1884 	.db 0x00
                                   1885 	.area CABS (ABS)

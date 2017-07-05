                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Jul  5 2014) (Linux)
                                      4 ; This file was generated Wed Jul  5 18:42:51 2017
                                      5 ;--------------------------------------------------------
                                      6 	.module se8r01_receive_pwm
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _main
                                     13 	.globl _Init_Tim2
                                     14 	.globl _SE8R01_Init
                                     15 	.globl _SE8R01_Analog_Init
                                     16 	.globl _SE8R01_Calibration
                                     17 	.globl _rf_switch_bank
                                     18 	.globl _init_io
                                     19 	.globl _InitializeUART
                                     20 	.globl _print_UCHAR_hex
                                     21 	.globl _UARTPrintF
                                     22 	.globl _delay
                                     23 	.globl _InitializeSystemClock
                                     24 	.globl _InitializeSPI
                                     25 	.globl _read_spi_buf
                                     26 	.globl _write_spi_buf
                                     27 	.globl _read_spi_reg
                                     28 	.globl _write_spi_reg
                                     29 	.globl _write_spi
                                     30 	.globl _delayTenMicro
                                     31 	.globl _memset
                                     32 	.globl _tx_buf
                                     33 	.globl _rx_buf
                                     34 	.globl _ADDRESS0
                                     35 	.globl _ADDRESS1
                                     36 	.globl _ADDRESS5
                                     37 	.globl _ADDRESS4
                                     38 	.globl _ADDRESS3
                                     39 	.globl _ADDRESS2
                                     40 	.globl _TX_ADDRESS
                                     41 	.globl _status
                                     42 	.globl _pip
                                     43 	.globl _signal_lv
                                     44 	.globl _newdata
                                     45 	.globl _pload_width_now
                                     46 	.globl _SE8R01_DR_500K
                                     47 	.globl _SE8R01_DR_1M
                                     48 	.globl _SE8R01_DR_2M
                                     49 	.globl _myData_pip4
                                     50 	.globl _myData_pip5
                                     51 	.globl _gtemp
                                     52 ;--------------------------------------------------------
                                     53 ; ram data
                                     54 ;--------------------------------------------------------
                                     55 	.area DATA
      000001                         56 _gtemp::
      000001                         57 	.ds 5
      000006                         58 _myData_pip5::
      000006                         59 	.ds 5
      00000B                         60 _myData_pip4::
      00000B                         61 	.ds 5
                                     62 ;--------------------------------------------------------
                                     63 ; ram data
                                     64 ;--------------------------------------------------------
                                     65 	.area INITIALIZED
      000010                         66 _SE8R01_DR_2M::
      000010                         67 	.ds 2
      000012                         68 _SE8R01_DR_1M::
      000012                         69 	.ds 2
      000014                         70 _SE8R01_DR_500K::
      000014                         71 	.ds 2
      000016                         72 _pload_width_now::
      000016                         73 	.ds 2
      000018                         74 _newdata::
      000018                         75 	.ds 2
      00001A                         76 _signal_lv::
      00001A                         77 	.ds 1
      00001B                         78 _pip::
      00001B                         79 	.ds 2
      00001D                         80 _status::
      00001D                         81 	.ds 1
      00001E                         82 _TX_ADDRESS::
      00001E                         83 	.ds 4
      000022                         84 _ADDRESS2::
      000022                         85 	.ds 1
      000023                         86 _ADDRESS3::
      000023                         87 	.ds 1
      000024                         88 _ADDRESS4::
      000024                         89 	.ds 1
      000025                         90 _ADDRESS5::
      000025                         91 	.ds 1
      000026                         92 _ADDRESS1::
      000026                         93 	.ds 4
      00002A                         94 _ADDRESS0::
      00002A                         95 	.ds 4
      00002E                         96 _rx_buf::
      00002E                         97 	.ds 32
      00004E                         98 _tx_buf::
      00004E                         99 	.ds 32
                                    100 ;--------------------------------------------------------
                                    101 ; Stack segment in internal ram 
                                    102 ;--------------------------------------------------------
                                    103 	.area	SSEG
      000000                        104 __start__stack:
      000000                        105 	.ds	1
                                    106 
                                    107 ;--------------------------------------------------------
                                    108 ; absolute external ram data
                                    109 ;--------------------------------------------------------
                                    110 	.area DABS (ABS)
                                    111 ;--------------------------------------------------------
                                    112 ; interrupt vector 
                                    113 ;--------------------------------------------------------
                                    114 	.area HOME
      008000                        115 __interrupt_vect:
      008000 82 00 80 83            116 	int s_GSINIT ;reset
      008004 82 00 00 00            117 	int 0x0000 ;trap
      008008 82 00 00 00            118 	int 0x0000 ;int0
      00800C 82 00 00 00            119 	int 0x0000 ;int1
      008010 82 00 00 00            120 	int 0x0000 ;int2
      008014 82 00 00 00            121 	int 0x0000 ;int3
      008018 82 00 00 00            122 	int 0x0000 ;int4
      00801C 82 00 00 00            123 	int 0x0000 ;int5
      008020 82 00 00 00            124 	int 0x0000 ;int6
      008024 82 00 00 00            125 	int 0x0000 ;int7
      008028 82 00 00 00            126 	int 0x0000 ;int8
      00802C 82 00 00 00            127 	int 0x0000 ;int9
      008030 82 00 00 00            128 	int 0x0000 ;int10
      008034 82 00 00 00            129 	int 0x0000 ;int11
      008038 82 00 00 00            130 	int 0x0000 ;int12
      00803C 82 00 00 00            131 	int 0x0000 ;int13
      008040 82 00 00 00            132 	int 0x0000 ;int14
      008044 82 00 00 00            133 	int 0x0000 ;int15
      008048 82 00 00 00            134 	int 0x0000 ;int16
      00804C 82 00 00 00            135 	int 0x0000 ;int17
      008050 82 00 00 00            136 	int 0x0000 ;int18
      008054 82 00 00 00            137 	int 0x0000 ;int19
      008058 82 00 00 00            138 	int 0x0000 ;int20
      00805C 82 00 00 00            139 	int 0x0000 ;int21
      008060 82 00 00 00            140 	int 0x0000 ;int22
      008064 82 00 00 00            141 	int 0x0000 ;int23
      008068 82 00 00 00            142 	int 0x0000 ;int24
      00806C 82 00 00 00            143 	int 0x0000 ;int25
      008070 82 00 00 00            144 	int 0x0000 ;int26
      008074 82 00 00 00            145 	int 0x0000 ;int27
      008078 82 00 00 00            146 	int 0x0000 ;int28
      00807C 82 00 00 00            147 	int 0x0000 ;int29
                                    148 ;--------------------------------------------------------
                                    149 ; global & static initialisations
                                    150 ;--------------------------------------------------------
                                    151 	.area HOME
                                    152 	.area GSINIT
                                    153 	.area GSFINAL
                                    154 	.area GSINIT
      008083                        155 __sdcc_gs_init_startup:
      008083                        156 __sdcc_init_data:
                                    157 ; stm8_genXINIT() start
      008083 AE 00 0F         [ 2]  158 	ldw x, #l_DATA
      008086 27 07            [ 1]  159 	jreq	00002$
      008088                        160 00001$:
      008088 72 4F 00 00      [ 1]  161 	clr (s_DATA - 1, x)
      00808C 5A               [ 2]  162 	decw x
      00808D 26 F9            [ 1]  163 	jrne	00001$
      00808F                        164 00002$:
      00808F AE 00 5E         [ 2]  165 	ldw	x, #l_INITIALIZER
      008092 27 09            [ 1]  166 	jreq	00004$
      008094                        167 00003$:
      008094 D6 8A 40         [ 1]  168 	ld	a, (s_INITIALIZER - 1, x)
      008097 D7 00 0F         [ 1]  169 	ld	(s_INITIALIZED - 1, x), a
      00809A 5A               [ 2]  170 	decw	x
      00809B 26 F7            [ 1]  171 	jrne	00003$
      00809D                        172 00004$:
                                    173 ; stm8_genXINIT() end
                                    174 	.area GSFINAL
      00809D CC 80 80         [ 2]  175 	jp	__sdcc_program_startup
                                    176 ;--------------------------------------------------------
                                    177 ; Home
                                    178 ;--------------------------------------------------------
                                    179 	.area HOME
                                    180 	.area HOME
      008080                        181 __sdcc_program_startup:
      008080 CC 87 FF         [ 2]  182 	jp	_main
                                    183 ;	return from main will return to caller
                                    184 ;--------------------------------------------------------
                                    185 ; code
                                    186 ;--------------------------------------------------------
                                    187 	.area CODE
                                    188 ;	se8r01-receive-pwm.c: 46: void delayTenMicro (void) {
                                    189 ;	-----------------------------------------
                                    190 ;	 function delayTenMicro
                                    191 ;	-----------------------------------------
      0080A0                        192 _delayTenMicro:
                                    193 ;	se8r01-receive-pwm.c: 48: for (a = 0; a < 50; ++a)
      0080A0 A6 32            [ 1]  194 	ld	a, #0x32
      0080A2                        195 00104$:
                                    196 ;	se8r01-receive-pwm.c: 49: __asm__("nop");
      0080A2 9D               [ 1]  197 	nop
      0080A3 4A               [ 1]  198 	dec	a
                                    199 ;	se8r01-receive-pwm.c: 48: for (a = 0; a < 50; ++a)
      0080A4 4D               [ 1]  200 	tnz	a
      0080A5 26 FB            [ 1]  201 	jrne	00104$
      0080A7 81               [ 4]  202 	ret
                                    203 ;	se8r01-receive-pwm.c: 51: UCHAR write_spi (UCHAR value) {
                                    204 ;	-----------------------------------------
                                    205 ;	 function write_spi
                                    206 ;	-----------------------------------------
      0080A8                        207 _write_spi:
                                    208 ;	se8r01-receive-pwm.c: 53: delayTenMicro ();
      0080A8 CD 80 A0         [ 4]  209 	call	_delayTenMicro
                                    210 ;	se8r01-receive-pwm.c: 54: SPI_DR = value;
      0080AB AE 52 04         [ 2]  211 	ldw	x, #0x5204
      0080AE 7B 03            [ 1]  212 	ld	a, (0x03, sp)
      0080B0 F7               [ 1]  213 	ld	(x), a
                                    214 ;	se8r01-receive-pwm.c: 55: delayTenMicro ();
      0080B1 CD 80 A0         [ 4]  215 	call	_delayTenMicro
                                    216 ;	se8r01-receive-pwm.c: 56: while ((SPI_SR & TXE) == 0);
      0080B4                        217 00101$:
      0080B4 AE 52 03         [ 2]  218 	ldw	x, #0x5203
      0080B7 F6               [ 1]  219 	ld	a, (x)
      0080B8 A5 02            [ 1]  220 	bcp	a, #0x02
      0080BA 27 F8            [ 1]  221 	jreq	00101$
                                    222 ;	se8r01-receive-pwm.c: 57: delayTenMicro ();
      0080BC CD 80 A0         [ 4]  223 	call	_delayTenMicro
                                    224 ;	se8r01-receive-pwm.c: 58: while ((SPI_SR & RXNE) == 0);
      0080BF                        225 00104$:
      0080BF AE 52 03         [ 2]  226 	ldw	x, #0x5203
      0080C2 F6               [ 1]  227 	ld	a, (x)
      0080C3 44               [ 1]  228 	srl	a
      0080C4 24 F9            [ 1]  229 	jrnc	00104$
                                    230 ;	se8r01-receive-pwm.c: 59: delayTenMicro ();
      0080C6 CD 80 A0         [ 4]  231 	call	_delayTenMicro
                                    232 ;	se8r01-receive-pwm.c: 60: ret = SPI_DR;
      0080C9 AE 52 04         [ 2]  233 	ldw	x, #0x5204
      0080CC F6               [ 1]  234 	ld	a, (x)
                                    235 ;	se8r01-receive-pwm.c: 61: return (ret);
      0080CD 81               [ 4]  236 	ret
                                    237 ;	se8r01-receive-pwm.c: 63: UCHAR write_spi_reg (UCHAR reg, UCHAR value) {
                                    238 ;	-----------------------------------------
                                    239 ;	 function write_spi_reg
                                    240 ;	-----------------------------------------
      0080CE                        241 _write_spi_reg:
      0080CE 88               [ 1]  242 	push	a
                                    243 ;	se8r01-receive-pwm.c: 65: PC_ODR &= ~(1 << CSN);
      0080CF AE 50 0A         [ 2]  244 	ldw	x, #0x500a
      0080D2 F6               [ 1]  245 	ld	a, (x)
      0080D3 A4 F7            [ 1]  246 	and	a, #0xf7
      0080D5 F7               [ 1]  247 	ld	(x), a
                                    248 ;	se8r01-receive-pwm.c: 66: ret = write_spi (reg);
      0080D6 7B 04            [ 1]  249 	ld	a, (0x04, sp)
      0080D8 88               [ 1]  250 	push	a
      0080D9 CD 80 A8         [ 4]  251 	call	_write_spi
      0080DC 5B 01            [ 2]  252 	addw	sp, #1
      0080DE 6B 01            [ 1]  253 	ld	(0x01, sp), a
                                    254 ;	se8r01-receive-pwm.c: 67: if (reg != NOP && reg != FLUSH_RX && reg != FLUSH_TX)
      0080E0 7B 04            [ 1]  255 	ld	a, (0x04, sp)
      0080E2 A1 FF            [ 1]  256 	cp	a, #0xff
      0080E4 27 15            [ 1]  257 	jreq	00102$
      0080E6 7B 04            [ 1]  258 	ld	a, (0x04, sp)
      0080E8 A1 E2            [ 1]  259 	cp	a, #0xe2
      0080EA 27 0F            [ 1]  260 	jreq	00102$
      0080EC 7B 04            [ 1]  261 	ld	a, (0x04, sp)
      0080EE A1 E1            [ 1]  262 	cp	a, #0xe1
      0080F0 27 09            [ 1]  263 	jreq	00102$
                                    264 ;	se8r01-receive-pwm.c: 68: write_spi (value);
      0080F2 7B 05            [ 1]  265 	ld	a, (0x05, sp)
      0080F4 88               [ 1]  266 	push	a
      0080F5 CD 80 A8         [ 4]  267 	call	_write_spi
      0080F8 84               [ 1]  268 	pop	a
      0080F9 20 03            [ 2]  269 	jra	00103$
      0080FB                        270 00102$:
                                    271 ;	se8r01-receive-pwm.c: 70: delayTenMicro ();
      0080FB CD 80 A0         [ 4]  272 	call	_delayTenMicro
      0080FE                        273 00103$:
                                    274 ;	se8r01-receive-pwm.c: 71: PC_ODR |= (1 << CSN);
      0080FE AE 50 0A         [ 2]  275 	ldw	x, #0x500a
      008101 F6               [ 1]  276 	ld	a, (x)
      008102 AA 08            [ 1]  277 	or	a, #0x08
      008104 F7               [ 1]  278 	ld	(x), a
                                    279 ;	se8r01-receive-pwm.c: 72: return (ret);
      008105 7B 01            [ 1]  280 	ld	a, (0x01, sp)
      008107 5B 01            [ 2]  281 	addw	sp, #1
      008109 81               [ 4]  282 	ret
                                    283 ;	se8r01-receive-pwm.c: 74: UCHAR read_spi_reg (UCHAR reg) {
                                    284 ;	-----------------------------------------
                                    285 ;	 function read_spi_reg
                                    286 ;	-----------------------------------------
      00810A                        287 _read_spi_reg:
      00810A 88               [ 1]  288 	push	a
                                    289 ;	se8r01-receive-pwm.c: 76: PC_ODR &= ~(1 << CSN);
      00810B AE 50 0A         [ 2]  290 	ldw	x, #0x500a
      00810E F6               [ 1]  291 	ld	a, (x)
      00810F A4 F7            [ 1]  292 	and	a, #0xf7
      008111 F7               [ 1]  293 	ld	(x), a
                                    294 ;	se8r01-receive-pwm.c: 77: ret = write_spi (reg);
      008112 7B 04            [ 1]  295 	ld	a, (0x04, sp)
      008114 88               [ 1]  296 	push	a
      008115 CD 80 A8         [ 4]  297 	call	_write_spi
      008118 5B 01            [ 2]  298 	addw	sp, #1
      00811A 6B 01            [ 1]  299 	ld	(0x01, sp), a
                                    300 ;	se8r01-receive-pwm.c: 78: if (reg != NOP && reg != FLUSH_RX && reg != FLUSH_TX)
      00811C 7B 04            [ 1]  301 	ld	a, (0x04, sp)
      00811E A1 FF            [ 1]  302 	cp	a, #0xff
      008120 27 17            [ 1]  303 	jreq	00102$
      008122 7B 04            [ 1]  304 	ld	a, (0x04, sp)
      008124 A1 E2            [ 1]  305 	cp	a, #0xe2
      008126 27 11            [ 1]  306 	jreq	00102$
      008128 7B 04            [ 1]  307 	ld	a, (0x04, sp)
      00812A A1 E1            [ 1]  308 	cp	a, #0xe1
      00812C 27 0B            [ 1]  309 	jreq	00102$
                                    310 ;	se8r01-receive-pwm.c: 79: ret = write_spi (NOP);
      00812E 4B FF            [ 1]  311 	push	#0xff
      008130 CD 80 A8         [ 4]  312 	call	_write_spi
      008133 5B 01            [ 2]  313 	addw	sp, #1
      008135 6B 01            [ 1]  314 	ld	(0x01, sp), a
      008137 20 03            [ 2]  315 	jra	00103$
      008139                        316 00102$:
                                    317 ;	se8r01-receive-pwm.c: 81: delayTenMicro ();
      008139 CD 80 A0         [ 4]  318 	call	_delayTenMicro
      00813C                        319 00103$:
                                    320 ;	se8r01-receive-pwm.c: 82: PC_ODR |= (1 << CSN);
      00813C AE 50 0A         [ 2]  321 	ldw	x, #0x500a
      00813F F6               [ 1]  322 	ld	a, (x)
      008140 AA 08            [ 1]  323 	or	a, #0x08
      008142 F7               [ 1]  324 	ld	(x), a
                                    325 ;	se8r01-receive-pwm.c: 83: return (ret);
      008143 7B 01            [ 1]  326 	ld	a, (0x01, sp)
      008145 5B 01            [ 2]  327 	addw	sp, #1
      008147 81               [ 4]  328 	ret
                                    329 ;	se8r01-receive-pwm.c: 85: UCHAR write_spi_buf (UCHAR reg, UCHAR *array, UCHAR len) {
                                    330 ;	-----------------------------------------
                                    331 ;	 function write_spi_buf
                                    332 ;	-----------------------------------------
      008148                        333 _write_spi_buf:
      008148 52 02            [ 2]  334 	sub	sp, #2
                                    335 ;	se8r01-receive-pwm.c: 87: PC_ODR &= ~(1 << CSN);
      00814A AE 50 0A         [ 2]  336 	ldw	x, #0x500a
      00814D F6               [ 1]  337 	ld	a, (x)
      00814E A4 F7            [ 1]  338 	and	a, #0xf7
      008150 F7               [ 1]  339 	ld	(x), a
                                    340 ;	se8r01-receive-pwm.c: 88: ret = write_spi (reg);
      008151 7B 05            [ 1]  341 	ld	a, (0x05, sp)
      008153 88               [ 1]  342 	push	a
      008154 CD 80 A8         [ 4]  343 	call	_write_spi
      008157 5B 01            [ 2]  344 	addw	sp, #1
      008159 6B 02            [ 1]  345 	ld	(0x02, sp), a
                                    346 ;	se8r01-receive-pwm.c: 89: for (n = 0; n < len; ++n)
      00815B 0F 01            [ 1]  347 	clr	(0x01, sp)
      00815D                        348 00103$:
      00815D 7B 01            [ 1]  349 	ld	a, (0x01, sp)
      00815F 11 08            [ 1]  350 	cp	a, (0x08, sp)
      008161 24 11            [ 1]  351 	jrnc	00101$
                                    352 ;	se8r01-receive-pwm.c: 90: write_spi (array[n]);
      008163 5F               [ 1]  353 	clrw	x
      008164 7B 01            [ 1]  354 	ld	a, (0x01, sp)
      008166 97               [ 1]  355 	ld	xl, a
      008167 72 FB 06         [ 2]  356 	addw	x, (0x06, sp)
      00816A F6               [ 1]  357 	ld	a, (x)
      00816B 88               [ 1]  358 	push	a
      00816C CD 80 A8         [ 4]  359 	call	_write_spi
      00816F 84               [ 1]  360 	pop	a
                                    361 ;	se8r01-receive-pwm.c: 89: for (n = 0; n < len; ++n)
      008170 0C 01            [ 1]  362 	inc	(0x01, sp)
      008172 20 E9            [ 2]  363 	jra	00103$
      008174                        364 00101$:
                                    365 ;	se8r01-receive-pwm.c: 91: PC_ODR |= (1 << CSN);
      008174 AE 50 0A         [ 2]  366 	ldw	x, #0x500a
      008177 F6               [ 1]  367 	ld	a, (x)
      008178 AA 08            [ 1]  368 	or	a, #0x08
      00817A F7               [ 1]  369 	ld	(x), a
                                    370 ;	se8r01-receive-pwm.c: 92: return (ret);
      00817B 7B 02            [ 1]  371 	ld	a, (0x02, sp)
      00817D 5B 02            [ 2]  372 	addw	sp, #2
      00817F 81               [ 4]  373 	ret
                                    374 ;	se8r01-receive-pwm.c: 94: UCHAR read_spi_buf (UCHAR reg, UCHAR *array, UCHAR len) {
                                    375 ;	-----------------------------------------
                                    376 ;	 function read_spi_buf
                                    377 ;	-----------------------------------------
      008180                        378 _read_spi_buf:
      008180 52 02            [ 2]  379 	sub	sp, #2
                                    380 ;	se8r01-receive-pwm.c: 96: PC_ODR &= ~(1 << CSN);
      008182 AE 50 0A         [ 2]  381 	ldw	x, #0x500a
      008185 F6               [ 1]  382 	ld	a, (x)
      008186 A4 F7            [ 1]  383 	and	a, #0xf7
      008188 F7               [ 1]  384 	ld	(x), a
                                    385 ;	se8r01-receive-pwm.c: 97: ret = write_spi (reg);
      008189 7B 05            [ 1]  386 	ld	a, (0x05, sp)
      00818B 88               [ 1]  387 	push	a
      00818C CD 80 A8         [ 4]  388 	call	_write_spi
      00818F 5B 01            [ 2]  389 	addw	sp, #1
      008191 6B 01            [ 1]  390 	ld	(0x01, sp), a
                                    391 ;	se8r01-receive-pwm.c: 98: for (n = 0; n < len; ++n)
      008193 0F 02            [ 1]  392 	clr	(0x02, sp)
      008195                        393 00103$:
      008195 7B 02            [ 1]  394 	ld	a, (0x02, sp)
      008197 11 08            [ 1]  395 	cp	a, (0x08, sp)
      008199 24 15            [ 1]  396 	jrnc	00101$
                                    397 ;	se8r01-receive-pwm.c: 99: array[n] = write_spi (NOP);
      00819B 5F               [ 1]  398 	clrw	x
      00819C 7B 02            [ 1]  399 	ld	a, (0x02, sp)
      00819E 97               [ 1]  400 	ld	xl, a
      00819F 72 FB 06         [ 2]  401 	addw	x, (0x06, sp)
      0081A2 89               [ 2]  402 	pushw	x
      0081A3 4B FF            [ 1]  403 	push	#0xff
      0081A5 CD 80 A8         [ 4]  404 	call	_write_spi
      0081A8 5B 01            [ 2]  405 	addw	sp, #1
      0081AA 85               [ 2]  406 	popw	x
      0081AB F7               [ 1]  407 	ld	(x), a
                                    408 ;	se8r01-receive-pwm.c: 98: for (n = 0; n < len; ++n)
      0081AC 0C 02            [ 1]  409 	inc	(0x02, sp)
      0081AE 20 E5            [ 2]  410 	jra	00103$
      0081B0                        411 00101$:
                                    412 ;	se8r01-receive-pwm.c: 100: PC_ODR |= (1 << CSN);
      0081B0 AE 50 0A         [ 2]  413 	ldw	x, #0x500a
      0081B3 F6               [ 1]  414 	ld	a, (x)
      0081B4 AA 08            [ 1]  415 	or	a, #0x08
      0081B6 F7               [ 1]  416 	ld	(x), a
                                    417 ;	se8r01-receive-pwm.c: 101: return (ret);
      0081B7 7B 01            [ 1]  418 	ld	a, (0x01, sp)
      0081B9 5B 02            [ 2]  419 	addw	sp, #2
      0081BB 81               [ 4]  420 	ret
                                    421 ;	se8r01-receive-pwm.c: 103: void InitializeSPI () {
                                    422 ;	-----------------------------------------
                                    423 ;	 function InitializeSPI
                                    424 ;	-----------------------------------------
      0081BC                        425 _InitializeSPI:
                                    426 ;	se8r01-receive-pwm.c: 104: SPI_CR1 = MSBFIRST | SPI_ENABLE | BR_DIV256 | MASTER | CPOL0 | CPHA0;
      0081BC AE 52 00         [ 2]  427 	ldw	x, #0x5200
      0081BF A6 7C            [ 1]  428 	ld	a, #0x7c
      0081C1 F7               [ 1]  429 	ld	(x), a
                                    430 ;	se8r01-receive-pwm.c: 105: SPI_CR2 = BDM_2LINE | CRCEN_OFF | CRCNEXT_TXBUF | FULL_DUPLEX | SSM_DISABLE;
      0081C2 AE 52 01         [ 2]  431 	ldw	x, #0x5201
      0081C5 7F               [ 1]  432 	clr	(x)
                                    433 ;	se8r01-receive-pwm.c: 106: SPI_ICR = TXIE_MASKED | RXIE_MASKED | ERRIE_MASKED | WKIE_MASKED;
      0081C6 AE 52 02         [ 2]  434 	ldw	x, #0x5202
      0081C9 7F               [ 1]  435 	clr	(x)
                                    436 ;	se8r01-receive-pwm.c: 107: PC_DDR = (1 << PC3) | (1 << PC4); // output mode
      0081CA AE 50 0C         [ 2]  437 	ldw	x, #0x500c
      0081CD A6 18            [ 1]  438 	ld	a, #0x18
      0081CF F7               [ 1]  439 	ld	(x), a
                                    440 ;	se8r01-receive-pwm.c: 108: PC_CR1 = (1 << PC3) | (1 << PC4); // push-pull
      0081D0 AE 50 0D         [ 2]  441 	ldw	x, #0x500d
      0081D3 A6 18            [ 1]  442 	ld	a, #0x18
      0081D5 F7               [ 1]  443 	ld	(x), a
                                    444 ;	se8r01-receive-pwm.c: 109: PC_CR2 = (1 << PC3) | (1 << PC4); // up to 10MHz speed
      0081D6 AE 50 0E         [ 2]  445 	ldw	x, #0x500e
      0081D9 A6 18            [ 1]  446 	ld	a, #0x18
      0081DB F7               [ 1]  447 	ld	(x), a
                                    448 ;	se8r01-receive-pwm.c: 111: PC_ODR &= ~(1 << CE);
      0081DC AE 50 0A         [ 2]  449 	ldw	x, #0x500a
      0081DF F6               [ 1]  450 	ld	a, (x)
      0081E0 A4 EF            [ 1]  451 	and	a, #0xef
      0081E2 F7               [ 1]  452 	ld	(x), a
      0081E3 81               [ 4]  453 	ret
                                    454 ;	se8r01-receive-pwm.c: 113: void InitializeSystemClock() {
                                    455 ;	-----------------------------------------
                                    456 ;	 function InitializeSystemClock
                                    457 ;	-----------------------------------------
      0081E4                        458 _InitializeSystemClock:
                                    459 ;	se8r01-receive-pwm.c: 114: CLK_ICKR = 0;                       //  Reset the Internal Clock Register.
      0081E4 AE 50 C0         [ 2]  460 	ldw	x, #0x50c0
      0081E7 7F               [ 1]  461 	clr	(x)
                                    462 ;	se8r01-receive-pwm.c: 115: CLK_ICKR = CLK_HSIEN;               //  Enable the HSI.
      0081E8 AE 50 C0         [ 2]  463 	ldw	x, #0x50c0
      0081EB A6 01            [ 1]  464 	ld	a, #0x01
      0081ED F7               [ 1]  465 	ld	(x), a
                                    466 ;	se8r01-receive-pwm.c: 116: CLK_ECKR = 0;                       //  Disable the external clock.
      0081EE AE 50 C1         [ 2]  467 	ldw	x, #0x50c1
      0081F1 7F               [ 1]  468 	clr	(x)
                                    469 ;	se8r01-receive-pwm.c: 117: while ((CLK_ICKR & CLK_HSIRDY) == 0);       //  Wait for the HSI to be ready for use.
      0081F2                        470 00101$:
      0081F2 AE 50 C0         [ 2]  471 	ldw	x, #0x50c0
      0081F5 F6               [ 1]  472 	ld	a, (x)
      0081F6 A5 02            [ 1]  473 	bcp	a, #0x02
      0081F8 27 F8            [ 1]  474 	jreq	00101$
                                    475 ;	se8r01-receive-pwm.c: 118: CLK_CKDIVR = 0;                     //  Ensure the clocks are running at full speed.
      0081FA AE 50 C6         [ 2]  476 	ldw	x, #0x50c6
      0081FD 7F               [ 1]  477 	clr	(x)
                                    478 ;	se8r01-receive-pwm.c: 119: CLK_PCKENR1 = 0xff;                 //  Enable all peripheral clocks.
      0081FE AE 50 C7         [ 2]  479 	ldw	x, #0x50c7
      008201 A6 FF            [ 1]  480 	ld	a, #0xff
      008203 F7               [ 1]  481 	ld	(x), a
                                    482 ;	se8r01-receive-pwm.c: 120: CLK_PCKENR2 = 0xff;                 //  Ditto.
      008204 AE 50 CA         [ 2]  483 	ldw	x, #0x50ca
      008207 A6 FF            [ 1]  484 	ld	a, #0xff
      008209 F7               [ 1]  485 	ld	(x), a
                                    486 ;	se8r01-receive-pwm.c: 121: CLK_CCOR = 0;                       //  Turn off CCO.
      00820A AE 50 C9         [ 2]  487 	ldw	x, #0x50c9
      00820D 7F               [ 1]  488 	clr	(x)
                                    489 ;	se8r01-receive-pwm.c: 122: CLK_HSITRIMR = 0;                   //  Turn off any HSIU trimming.
      00820E AE 50 CC         [ 2]  490 	ldw	x, #0x50cc
      008211 7F               [ 1]  491 	clr	(x)
                                    492 ;	se8r01-receive-pwm.c: 123: CLK_SWIMCCR = 0;                    //  Set SWIM to run at clock / 2.
      008212 AE 50 CD         [ 2]  493 	ldw	x, #0x50cd
      008215 7F               [ 1]  494 	clr	(x)
                                    495 ;	se8r01-receive-pwm.c: 124: CLK_SWR = 0xe1;                     //  Use HSI as the clock source.
      008216 AE 50 C4         [ 2]  496 	ldw	x, #0x50c4
      008219 A6 E1            [ 1]  497 	ld	a, #0xe1
      00821B F7               [ 1]  498 	ld	(x), a
                                    499 ;	se8r01-receive-pwm.c: 125: CLK_SWCR = 0;                       //  Reset the clock switch control register.
      00821C AE 50 C5         [ 2]  500 	ldw	x, #0x50c5
      00821F 7F               [ 1]  501 	clr	(x)
                                    502 ;	se8r01-receive-pwm.c: 126: CLK_SWCR = CLK_SWEN;                //  Enable switching.
      008220 AE 50 C5         [ 2]  503 	ldw	x, #0x50c5
      008223 A6 02            [ 1]  504 	ld	a, #0x02
      008225 F7               [ 1]  505 	ld	(x), a
                                    506 ;	se8r01-receive-pwm.c: 127: while ((CLK_SWCR & CLK_SWBSY) != 0);        //  Pause while the clock switch is busy.
      008226                        507 00104$:
      008226 AE 50 C5         [ 2]  508 	ldw	x, #0x50c5
      008229 F6               [ 1]  509 	ld	a, (x)
      00822A 44               [ 1]  510 	srl	a
      00822B 25 F9            [ 1]  511 	jrc	00104$
      00822D 81               [ 4]  512 	ret
                                    513 ;	se8r01-receive-pwm.c: 129: void delay (int time_ms) {
                                    514 ;	-----------------------------------------
                                    515 ;	 function delay
                                    516 ;	-----------------------------------------
      00822E                        517 _delay:
      00822E 52 0A            [ 2]  518 	sub	sp, #10
                                    519 ;	se8r01-receive-pwm.c: 131: for (x = 0; x < 1036*time_ms; ++x)
      008230 5F               [ 1]  520 	clrw	x
      008231 1F 03            [ 2]  521 	ldw	(0x03, sp), x
      008233 1F 01            [ 2]  522 	ldw	(0x01, sp), x
      008235 1E 0D            [ 2]  523 	ldw	x, (0x0d, sp)
      008237 89               [ 2]  524 	pushw	x
      008238 4B 0C            [ 1]  525 	push	#0x0c
      00823A 4B 04            [ 1]  526 	push	#0x04
      00823C CD 89 CC         [ 4]  527 	call	__mulint
      00823F 5B 04            [ 2]  528 	addw	sp, #4
      008241 1F 09            [ 2]  529 	ldw	(0x09, sp), x
      008243                        530 00103$:
      008243 16 09            [ 2]  531 	ldw	y, (0x09, sp)
      008245 17 07            [ 2]  532 	ldw	(0x07, sp), y
      008247 7B 07            [ 1]  533 	ld	a, (0x07, sp)
      008249 49               [ 1]  534 	rlc	a
      00824A 4F               [ 1]  535 	clr	a
      00824B A2 00            [ 1]  536 	sbc	a, #0x00
      00824D 6B 06            [ 1]  537 	ld	(0x06, sp), a
      00824F 6B 05            [ 1]  538 	ld	(0x05, sp), a
      008251 1E 03            [ 2]  539 	ldw	x, (0x03, sp)
      008253 13 07            [ 2]  540 	cpw	x, (0x07, sp)
      008255 7B 02            [ 1]  541 	ld	a, (0x02, sp)
      008257 12 06            [ 1]  542 	sbc	a, (0x06, sp)
      008259 7B 01            [ 1]  543 	ld	a, (0x01, sp)
      00825B 12 05            [ 1]  544 	sbc	a, (0x05, sp)
      00825D 2E 17            [ 1]  545 	jrsge	00105$
                                    546 ;	se8r01-receive-pwm.c: 132: __asm__("nop");
      00825F 9D               [ 1]  547 	nop
                                    548 ;	se8r01-receive-pwm.c: 131: for (x = 0; x < 1036*time_ms; ++x)
      008260 16 03            [ 2]  549 	ldw	y, (0x03, sp)
      008262 72 A9 00 01      [ 2]  550 	addw	y, #0x0001
      008266 7B 02            [ 1]  551 	ld	a, (0x02, sp)
      008268 A9 00            [ 1]  552 	adc	a, #0x00
      00826A 97               [ 1]  553 	ld	xl, a
      00826B 7B 01            [ 1]  554 	ld	a, (0x01, sp)
      00826D A9 00            [ 1]  555 	adc	a, #0x00
      00826F 95               [ 1]  556 	ld	xh, a
      008270 17 03            [ 2]  557 	ldw	(0x03, sp), y
      008272 1F 01            [ 2]  558 	ldw	(0x01, sp), x
      008274 20 CD            [ 2]  559 	jra	00103$
      008276                        560 00105$:
      008276 5B 0A            [ 2]  561 	addw	sp, #10
      008278 81               [ 4]  562 	ret
                                    563 ;	se8r01-receive-pwm.c: 137: void UARTPrintF (char *message) {
                                    564 ;	-----------------------------------------
                                    565 ;	 function UARTPrintF
                                    566 ;	-----------------------------------------
      008279                        567 _UARTPrintF:
                                    568 ;	se8r01-receive-pwm.c: 138: char *ch = message;
      008279 16 03            [ 2]  569 	ldw	y, (0x03, sp)
                                    570 ;	se8r01-receive-pwm.c: 139: while (*ch) {
      00827B                        571 00104$:
      00827B 90 F6            [ 1]  572 	ld	a, (y)
      00827D 4D               [ 1]  573 	tnz	a
      00827E 27 0F            [ 1]  574 	jreq	00107$
                                    575 ;	se8r01-receive-pwm.c: 140: UART1_DR = (unsigned char) *ch;     //  Put the next character into the data transmission register.
      008280 AE 52 31         [ 2]  576 	ldw	x, #0x5231
      008283 F7               [ 1]  577 	ld	(x), a
                                    578 ;	se8r01-receive-pwm.c: 141: while ((UART1_SR & SR_TXE) == 0);   //  Wait for transmission to complete.
      008284                        579 00101$:
      008284 AE 52 30         [ 2]  580 	ldw	x, #0x5230
      008287 F6               [ 1]  581 	ld	a, (x)
      008288 48               [ 1]  582 	sll	a
      008289 24 F9            [ 1]  583 	jrnc	00101$
                                    584 ;	se8r01-receive-pwm.c: 142: ch++;                               //  Grab the next character.
      00828B 90 5C            [ 2]  585 	incw	y
      00828D 20 EC            [ 2]  586 	jra	00104$
      00828F                        587 00107$:
      00828F 81               [ 4]  588 	ret
                                    589 ;	se8r01-receive-pwm.c: 145: void print_UCHAR_hex (unsigned char buffer) {
                                    590 ;	-----------------------------------------
                                    591 ;	 function print_UCHAR_hex
                                    592 ;	-----------------------------------------
      008290                        593 _print_UCHAR_hex:
      008290 52 0C            [ 2]  594 	sub	sp, #12
                                    595 ;	se8r01-receive-pwm.c: 148: a = (buffer >> 4);
      008292 7B 0F            [ 1]  596 	ld	a, (0x0f, sp)
      008294 4E               [ 1]  597 	swap	a
      008295 A4 0F            [ 1]  598 	and	a, #0x0f
      008297 5F               [ 1]  599 	clrw	x
      008298 97               [ 1]  600 	ld	xl, a
                                    601 ;	se8r01-receive-pwm.c: 149: if (a > 9)
      008299 A3 00 09         [ 2]  602 	cpw	x, #0x0009
      00829C 2D 07            [ 1]  603 	jrsle	00102$
                                    604 ;	se8r01-receive-pwm.c: 150: a = a + 'a' - 10;
      00829E 1C 00 57         [ 2]  605 	addw	x, #0x0057
      0082A1 1F 0B            [ 2]  606 	ldw	(0x0b, sp), x
      0082A3 20 05            [ 2]  607 	jra	00103$
      0082A5                        608 00102$:
                                    609 ;	se8r01-receive-pwm.c: 152: a += '0'; 
      0082A5 1C 00 30         [ 2]  610 	addw	x, #0x0030
      0082A8 1F 0B            [ 2]  611 	ldw	(0x0b, sp), x
      0082AA                        612 00103$:
                                    613 ;	se8r01-receive-pwm.c: 153: b = buffer & 0x0f;
      0082AA 7B 0F            [ 1]  614 	ld	a, (0x0f, sp)
      0082AC A4 0F            [ 1]  615 	and	a, #0x0f
      0082AE 5F               [ 1]  616 	clrw	x
      0082AF 97               [ 1]  617 	ld	xl, a
                                    618 ;	se8r01-receive-pwm.c: 154: if (b > 9)
      0082B0 A3 00 09         [ 2]  619 	cpw	x, #0x0009
      0082B3 2D 07            [ 1]  620 	jrsle	00105$
                                    621 ;	se8r01-receive-pwm.c: 155: b = b + 'a' - 10;
      0082B5 1C 00 57         [ 2]  622 	addw	x, #0x0057
      0082B8 1F 09            [ 2]  623 	ldw	(0x09, sp), x
      0082BA 20 05            [ 2]  624 	jra	00106$
      0082BC                        625 00105$:
                                    626 ;	se8r01-receive-pwm.c: 157: b += '0'; 
      0082BC 1C 00 30         [ 2]  627 	addw	x, #0x0030
      0082BF 1F 09            [ 2]  628 	ldw	(0x09, sp), x
      0082C1                        629 00106$:
                                    630 ;	se8r01-receive-pwm.c: 158: message[0] = a;
      0082C1 90 96            [ 1]  631 	ldw	y, sp
      0082C3 90 5C            [ 2]  632 	incw	y
      0082C5 7B 0C            [ 1]  633 	ld	a, (0x0c, sp)
      0082C7 90 F7            [ 1]  634 	ld	(y), a
                                    635 ;	se8r01-receive-pwm.c: 159: message[1] = b;
      0082C9 93               [ 1]  636 	ldw	x, y
      0082CA 5C               [ 2]  637 	incw	x
      0082CB 7B 0A            [ 1]  638 	ld	a, (0x0a, sp)
      0082CD F7               [ 1]  639 	ld	(x), a
                                    640 ;	se8r01-receive-pwm.c: 160: message[2] = 0;
      0082CE 93               [ 1]  641 	ldw	x, y
      0082CF 5C               [ 2]  642 	incw	x
      0082D0 5C               [ 2]  643 	incw	x
      0082D1 7F               [ 1]  644 	clr	(x)
                                    645 ;	se8r01-receive-pwm.c: 161: UARTPrintF (message);
      0082D2 90 89            [ 2]  646 	pushw	y
      0082D4 CD 82 79         [ 4]  647 	call	_UARTPrintF
      0082D7 5B 02            [ 2]  648 	addw	sp, #2
      0082D9 5B 0C            [ 2]  649 	addw	sp, #12
      0082DB 81               [ 4]  650 	ret
                                    651 ;	se8r01-receive-pwm.c: 164: void InitializeUART() {
                                    652 ;	-----------------------------------------
                                    653 ;	 function InitializeUART
                                    654 ;	-----------------------------------------
      0082DC                        655 _InitializeUART:
                                    656 ;	se8r01-receive-pwm.c: 174: UART1_CR1 = 0;
      0082DC AE 52 34         [ 2]  657 	ldw	x, #0x5234
      0082DF 7F               [ 1]  658 	clr	(x)
                                    659 ;	se8r01-receive-pwm.c: 175: UART1_CR2 = 0;
      0082E0 AE 52 35         [ 2]  660 	ldw	x, #0x5235
      0082E3 7F               [ 1]  661 	clr	(x)
                                    662 ;	se8r01-receive-pwm.c: 176: UART1_CR4 = 0;
      0082E4 AE 52 37         [ 2]  663 	ldw	x, #0x5237
      0082E7 7F               [ 1]  664 	clr	(x)
                                    665 ;	se8r01-receive-pwm.c: 177: UART1_CR3 = 0;
      0082E8 AE 52 36         [ 2]  666 	ldw	x, #0x5236
      0082EB 7F               [ 1]  667 	clr	(x)
                                    668 ;	se8r01-receive-pwm.c: 178: UART1_CR5 = 0;
      0082EC AE 52 38         [ 2]  669 	ldw	x, #0x5238
      0082EF 7F               [ 1]  670 	clr	(x)
                                    671 ;	se8r01-receive-pwm.c: 179: UART1_GTR = 0;
      0082F0 AE 52 39         [ 2]  672 	ldw	x, #0x5239
      0082F3 7F               [ 1]  673 	clr	(x)
                                    674 ;	se8r01-receive-pwm.c: 180: UART1_PSCR = 0;
      0082F4 AE 52 3A         [ 2]  675 	ldw	x, #0x523a
      0082F7 7F               [ 1]  676 	clr	(x)
                                    677 ;	se8r01-receive-pwm.c: 184: UNSET (UART1_CR1, CR1_M);        //  8 Data bits.
      0082F8 AE 52 34         [ 2]  678 	ldw	x, #0x5234
      0082FB F6               [ 1]  679 	ld	a, (x)
      0082FC A4 EF            [ 1]  680 	and	a, #0xef
      0082FE F7               [ 1]  681 	ld	(x), a
                                    682 ;	se8r01-receive-pwm.c: 185: UNSET (UART1_CR1, CR1_PCEN);     //  Disable parity.
      0082FF AE 52 34         [ 2]  683 	ldw	x, #0x5234
      008302 F6               [ 1]  684 	ld	a, (x)
      008303 A4 FB            [ 1]  685 	and	a, #0xfb
      008305 F7               [ 1]  686 	ld	(x), a
                                    687 ;	se8r01-receive-pwm.c: 186: UNSET (UART1_CR3, CR3_STOPH);    //  1 stop bit.
      008306 AE 52 36         [ 2]  688 	ldw	x, #0x5236
      008309 F6               [ 1]  689 	ld	a, (x)
      00830A A4 DF            [ 1]  690 	and	a, #0xdf
      00830C F7               [ 1]  691 	ld	(x), a
                                    692 ;	se8r01-receive-pwm.c: 187: UNSET (UART1_CR3, CR3_STOPL);    //  1 stop bit.
      00830D AE 52 36         [ 2]  693 	ldw	x, #0x5236
      008310 F6               [ 1]  694 	ld	a, (x)
      008311 A4 EF            [ 1]  695 	and	a, #0xef
      008313 F7               [ 1]  696 	ld	(x), a
                                    697 ;	se8r01-receive-pwm.c: 188: UART1_BRR2 = 0x0a;      //  Set the baud rate registers to 115200 baud
      008314 AE 52 33         [ 2]  698 	ldw	x, #0x5233
      008317 A6 0A            [ 1]  699 	ld	a, #0x0a
      008319 F7               [ 1]  700 	ld	(x), a
                                    701 ;	se8r01-receive-pwm.c: 189: UART1_BRR1 = 0x08;      //  based upon a 16 MHz system clock.
      00831A AE 52 32         [ 2]  702 	ldw	x, #0x5232
      00831D A6 08            [ 1]  703 	ld	a, #0x08
      00831F F7               [ 1]  704 	ld	(x), a
                                    705 ;	se8r01-receive-pwm.c: 193: UNSET (UART1_CR2, CR2_TEN);      //  Disable transmit.
      008320 AE 52 35         [ 2]  706 	ldw	x, #0x5235
      008323 F6               [ 1]  707 	ld	a, (x)
      008324 A4 F7            [ 1]  708 	and	a, #0xf7
      008326 F7               [ 1]  709 	ld	(x), a
                                    710 ;	se8r01-receive-pwm.c: 194: UNSET (UART1_CR2, CR2_REN);      //  Disable receive.
      008327 AE 52 35         [ 2]  711 	ldw	x, #0x5235
      00832A F6               [ 1]  712 	ld	a, (x)
      00832B A4 FB            [ 1]  713 	and	a, #0xfb
      00832D F7               [ 1]  714 	ld	(x), a
                                    715 ;	se8r01-receive-pwm.c: 198: SET (UART1_CR3, CR3_CPOL);
      00832E AE 52 36         [ 2]  716 	ldw	x, #0x5236
      008331 F6               [ 1]  717 	ld	a, (x)
      008332 AA 04            [ 1]  718 	or	a, #0x04
      008334 F7               [ 1]  719 	ld	(x), a
                                    720 ;	se8r01-receive-pwm.c: 199: SET (UART1_CR3, CR3_CPHA);
      008335 AE 52 36         [ 2]  721 	ldw	x, #0x5236
      008338 F6               [ 1]  722 	ld	a, (x)
      008339 AA 02            [ 1]  723 	or	a, #0x02
      00833B F7               [ 1]  724 	ld	(x), a
                                    725 ;	se8r01-receive-pwm.c: 200: SET (UART1_CR3, CR3_LBCL);
      00833C 72 10 52 36      [ 1]  726 	bset	0x5236, #0
                                    727 ;	se8r01-receive-pwm.c: 204: SET (UART1_CR2, CR2_TEN);
      008340 AE 52 35         [ 2]  728 	ldw	x, #0x5235
      008343 F6               [ 1]  729 	ld	a, (x)
      008344 AA 08            [ 1]  730 	or	a, #0x08
      008346 F7               [ 1]  731 	ld	(x), a
                                    732 ;	se8r01-receive-pwm.c: 205: SET (UART1_CR2, CR2_REN);
      008347 AE 52 35         [ 2]  733 	ldw	x, #0x5235
      00834A F6               [ 1]  734 	ld	a, (x)
      00834B AA 04            [ 1]  735 	or	a, #0x04
      00834D F7               [ 1]  736 	ld	(x), a
                                    737 ;	se8r01-receive-pwm.c: 206: UART1_CR3 = CR3_CLKEN;
      00834E AE 52 36         [ 2]  738 	ldw	x, #0x5236
      008351 A6 08            [ 1]  739 	ld	a, #0x08
      008353 F7               [ 1]  740 	ld	(x), a
      008354 81               [ 4]  741 	ret
                                    742 ;	se8r01-receive-pwm.c: 279: void init_io(void)
                                    743 ;	-----------------------------------------
                                    744 ;	 function init_io
                                    745 ;	-----------------------------------------
      008355                        746 _init_io:
                                    747 ;	se8r01-receive-pwm.c: 281: PD_DDR &= ~(1 << 3); // input mode
      008355 AE 50 11         [ 2]  748 	ldw	x, #0x5011
      008358 F6               [ 1]  749 	ld	a, (x)
      008359 A4 F7            [ 1]  750 	and	a, #0xf7
      00835B F7               [ 1]  751 	ld	(x), a
                                    752 ;	se8r01-receive-pwm.c: 282: PD_CR1 |= (1 << 3); // input with pull up 
      00835C AE 50 12         [ 2]  753 	ldw	x, #0x5012
      00835F F6               [ 1]  754 	ld	a, (x)
      008360 AA 08            [ 1]  755 	or	a, #0x08
      008362 F7               [ 1]  756 	ld	(x), a
                                    757 ;	se8r01-receive-pwm.c: 283: PD_CR2 |= (1 << 3); // interrupt enabled 
      008363 AE 50 13         [ 2]  758 	ldw	x, #0x5013
      008366 F6               [ 1]  759 	ld	a, (x)
      008367 AA 08            [ 1]  760 	or	a, #0x08
      008369 F7               [ 1]  761 	ld	(x), a
                                    762 ;	se8r01-receive-pwm.c: 287: PC_ODR &= ~(1 << CE);
      00836A AE 50 0A         [ 2]  763 	ldw	x, #0x500a
      00836D F6               [ 1]  764 	ld	a, (x)
      00836E A4 EF            [ 1]  765 	and	a, #0xef
      008370 F7               [ 1]  766 	ld	(x), a
                                    767 ;	se8r01-receive-pwm.c: 289: PC_ODR |= (1 << CSN);
      008371 AE 50 0A         [ 2]  768 	ldw	x, #0x500a
      008374 F6               [ 1]  769 	ld	a, (x)
      008375 AA 08            [ 1]  770 	or	a, #0x08
      008377 F7               [ 1]  771 	ld	(x), a
      008378 81               [ 4]  772 	ret
                                    773 ;	se8r01-receive-pwm.c: 295: void rf_switch_bank(unsigned char bankindex)
                                    774 ;	-----------------------------------------
                                    775 ;	 function rf_switch_bank
                                    776 ;	-----------------------------------------
      008379                        777 _rf_switch_bank:
      008379 88               [ 1]  778 	push	a
                                    779 ;	se8r01-receive-pwm.c: 298: temp1 = bankindex;
      00837A 7B 04            [ 1]  780 	ld	a, (0x04, sp)
      00837C 6B 01            [ 1]  781 	ld	(0x01, sp), a
                                    782 ;	se8r01-receive-pwm.c: 300: temp0 = write_spi(iRF_BANK0_STATUS);
      00837E 4B 07            [ 1]  783 	push	#0x07
      008380 CD 80 A8         [ 4]  784 	call	_write_spi
      008383 5B 01            [ 2]  785 	addw	sp, #1
                                    786 ;	se8r01-receive-pwm.c: 302: if((temp0&0x80)!=temp1)
      008385 A4 80            [ 1]  787 	and	a, #0x80
      008387 11 01            [ 1]  788 	cp	a, (0x01, sp)
      008389 27 09            [ 1]  789 	jreq	00103$
                                    790 ;	se8r01-receive-pwm.c: 304: write_spi_reg(iRF_CMD_ACTIVATE,0x53);
      00838B 4B 53            [ 1]  791 	push	#0x53
      00838D 4B 50            [ 1]  792 	push	#0x50
      00838F CD 80 CE         [ 4]  793 	call	_write_spi_reg
      008392 5B 02            [ 2]  794 	addw	sp, #2
      008394                        795 00103$:
      008394 84               [ 1]  796 	pop	a
      008395 81               [ 4]  797 	ret
                                    798 ;	se8r01-receive-pwm.c: 311: void SE8R01_Calibration()
                                    799 ;	-----------------------------------------
                                    800 ;	 function SE8R01_Calibration
                                    801 ;	-----------------------------------------
      008396                        802 _SE8R01_Calibration:
      008396 52 0D            [ 2]  803 	sub	sp, #13
                                    804 ;	se8r01-receive-pwm.c: 314: rf_switch_bank(iBANK0);
      008398 4B 00            [ 1]  805 	push	#0x00
      00839A CD 83 79         [ 4]  806 	call	_rf_switch_bank
      00839D 84               [ 1]  807 	pop	a
                                    808 ;	se8r01-receive-pwm.c: 315: temp[0]=0x03;
      00839E 96               [ 1]  809 	ldw	x, sp
      00839F 5C               [ 2]  810 	incw	x
      0083A0 1F 06            [ 2]  811 	ldw	(0x06, sp), x
      0083A2 1E 06            [ 2]  812 	ldw	x, (0x06, sp)
      0083A4 A6 03            [ 1]  813 	ld	a, #0x03
      0083A6 F7               [ 1]  814 	ld	(x), a
                                    815 ;	se8r01-receive-pwm.c: 316: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_CONFIG,temp, 1);
      0083A7 1E 06            [ 2]  816 	ldw	x, (0x06, sp)
      0083A9 4B 01            [ 1]  817 	push	#0x01
      0083AB 89               [ 2]  818 	pushw	x
      0083AC 4B 20            [ 1]  819 	push	#0x20
      0083AE CD 81 48         [ 4]  820 	call	_write_spi_buf
      0083B1 5B 04            [ 2]  821 	addw	sp, #4
                                    822 ;	se8r01-receive-pwm.c: 318: temp[0]=0x32;
      0083B3 1E 06            [ 2]  823 	ldw	x, (0x06, sp)
      0083B5 A6 32            [ 1]  824 	ld	a, #0x32
      0083B7 F7               [ 1]  825 	ld	(x), a
                                    826 ;	se8r01-receive-pwm.c: 320: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_CH, temp,1);
      0083B8 1E 06            [ 2]  827 	ldw	x, (0x06, sp)
      0083BA 4B 01            [ 1]  828 	push	#0x01
      0083BC 89               [ 2]  829 	pushw	x
      0083BD 4B 25            [ 1]  830 	push	#0x25
      0083BF CD 81 48         [ 4]  831 	call	_write_spi_buf
      0083C2 5B 04            [ 2]  832 	addw	sp, #4
                                    833 ;	se8r01-receive-pwm.c: 324: if (SE8R01_DR_2M==1)
      0083C4 CE 00 10         [ 2]  834 	ldw	x, _SE8R01_DR_2M+0
      0083C7 A3 00 01         [ 2]  835 	cpw	x, #0x0001
      0083CA 26 07            [ 1]  836 	jrne	00105$
                                    837 ;	se8r01-receive-pwm.c: 325: {temp[0]=0x48;}
      0083CC 1E 06            [ 2]  838 	ldw	x, (0x06, sp)
      0083CE A6 48            [ 1]  839 	ld	a, #0x48
      0083D0 F7               [ 1]  840 	ld	(x), a
      0083D1 20 14            [ 2]  841 	jra	00106$
      0083D3                        842 00105$:
                                    843 ;	se8r01-receive-pwm.c: 326: else if (SE8R01_DR_1M==1)
      0083D3 CE 00 12         [ 2]  844 	ldw	x, _SE8R01_DR_1M+0
      0083D6 A3 00 01         [ 2]  845 	cpw	x, #0x0001
      0083D9 26 07            [ 1]  846 	jrne	00102$
                                    847 ;	se8r01-receive-pwm.c: 327: {temp[0]=0x40;}
      0083DB 1E 06            [ 2]  848 	ldw	x, (0x06, sp)
      0083DD A6 40            [ 1]  849 	ld	a, #0x40
      0083DF F7               [ 1]  850 	ld	(x), a
      0083E0 20 05            [ 2]  851 	jra	00106$
      0083E2                        852 00102$:
                                    853 ;	se8r01-receive-pwm.c: 329: {temp[0]=0x68;}   
      0083E2 1E 06            [ 2]  854 	ldw	x, (0x06, sp)
      0083E4 A6 68            [ 1]  855 	ld	a, #0x68
      0083E6 F7               [ 1]  856 	ld	(x), a
      0083E7                        857 00106$:
                                    858 ;	se8r01-receive-pwm.c: 331: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_SETUP,temp,1);
      0083E7 1E 06            [ 2]  859 	ldw	x, (0x06, sp)
      0083E9 4B 01            [ 1]  860 	push	#0x01
      0083EB 89               [ 2]  861 	pushw	x
      0083EC 4B 26            [ 1]  862 	push	#0x26
      0083EE CD 81 48         [ 4]  863 	call	_write_spi_buf
      0083F1 5B 04            [ 2]  864 	addw	sp, #4
                                    865 ;	se8r01-receive-pwm.c: 332: temp[0]=0x77;
      0083F3 1E 06            [ 2]  866 	ldw	x, (0x06, sp)
      0083F5 A6 77            [ 1]  867 	ld	a, #0x77
      0083F7 F7               [ 1]  868 	ld	(x), a
                                    869 ;	se8r01-receive-pwm.c: 333: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_PRE_GURD, temp,1);
      0083F8 1E 06            [ 2]  870 	ldw	x, (0x06, sp)
      0083FA 4B 01            [ 1]  871 	push	#0x01
      0083FC 89               [ 2]  872 	pushw	x
      0083FD 4B 3F            [ 1]  873 	push	#0x3f
      0083FF CD 81 48         [ 4]  874 	call	_write_spi_buf
      008402 5B 04            [ 2]  875 	addw	sp, #4
                                    876 ;	se8r01-receive-pwm.c: 335: rf_switch_bank(iBANK1);
      008404 4B 80            [ 1]  877 	push	#0x80
      008406 CD 83 79         [ 4]  878 	call	_rf_switch_bank
      008409 84               [ 1]  879 	pop	a
                                    880 ;	se8r01-receive-pwm.c: 336: temp[0]=0x40;
      00840A 1E 06            [ 2]  881 	ldw	x, (0x06, sp)
      00840C A6 40            [ 1]  882 	ld	a, #0x40
      00840E F7               [ 1]  883 	ld	(x), a
                                    884 ;	se8r01-receive-pwm.c: 337: temp[1]=0x00;
      00840F 1E 06            [ 2]  885 	ldw	x, (0x06, sp)
      008411 5C               [ 2]  886 	incw	x
      008412 1F 0C            [ 2]  887 	ldw	(0x0c, sp), x
      008414 1E 0C            [ 2]  888 	ldw	x, (0x0c, sp)
      008416 7F               [ 1]  889 	clr	(x)
                                    890 ;	se8r01-receive-pwm.c: 338: temp[2]=0x10;
      008417 1E 06            [ 2]  891 	ldw	x, (0x06, sp)
      008419 5C               [ 2]  892 	incw	x
      00841A 5C               [ 2]  893 	incw	x
      00841B 1F 0A            [ 2]  894 	ldw	(0x0a, sp), x
      00841D 1E 0A            [ 2]  895 	ldw	x, (0x0a, sp)
      00841F A6 10            [ 1]  896 	ld	a, #0x10
      008421 F7               [ 1]  897 	ld	(x), a
                                    898 ;	se8r01-receive-pwm.c: 340: {temp[3]=0xE6;}
      008422 1E 06            [ 2]  899 	ldw	x, (0x06, sp)
      008424 1C 00 03         [ 2]  900 	addw	x, #0x0003
      008427 1F 08            [ 2]  901 	ldw	(0x08, sp), x
                                    902 ;	se8r01-receive-pwm.c: 339: if (SE8R01_DR_2M==1)
      008429 CE 00 10         [ 2]  903 	ldw	x, _SE8R01_DR_2M+0
      00842C A3 00 01         [ 2]  904 	cpw	x, #0x0001
      00842F 26 07            [ 1]  905 	jrne	00108$
                                    906 ;	se8r01-receive-pwm.c: 340: {temp[3]=0xE6;}
      008431 1E 08            [ 2]  907 	ldw	x, (0x08, sp)
      008433 A6 E6            [ 1]  908 	ld	a, #0xe6
      008435 F7               [ 1]  909 	ld	(x), a
      008436 20 05            [ 2]  910 	jra	00109$
      008438                        911 00108$:
                                    912 ;	se8r01-receive-pwm.c: 342: {temp[3]=0xE4;}
      008438 1E 08            [ 2]  913 	ldw	x, (0x08, sp)
      00843A A6 E4            [ 1]  914 	ld	a, #0xe4
      00843C F7               [ 1]  915 	ld	(x), a
      00843D                        916 00109$:
                                    917 ;	se8r01-receive-pwm.c: 344: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_PLL_CTL0, temp, 4);
      00843D 1E 06            [ 2]  918 	ldw	x, (0x06, sp)
      00843F 4B 04            [ 1]  919 	push	#0x04
      008441 89               [ 2]  920 	pushw	x
      008442 4B 21            [ 1]  921 	push	#0x21
      008444 CD 81 48         [ 4]  922 	call	_write_spi_buf
      008447 5B 04            [ 2]  923 	addw	sp, #4
                                    924 ;	se8r01-receive-pwm.c: 346: temp[0]=0x20;
      008449 1E 06            [ 2]  925 	ldw	x, (0x06, sp)
      00844B A6 20            [ 1]  926 	ld	a, #0x20
      00844D F7               [ 1]  927 	ld	(x), a
                                    928 ;	se8r01-receive-pwm.c: 347: temp[1]=0x08;
      00844E 1E 0C            [ 2]  929 	ldw	x, (0x0c, sp)
      008450 A6 08            [ 1]  930 	ld	a, #0x08
      008452 F7               [ 1]  931 	ld	(x), a
                                    932 ;	se8r01-receive-pwm.c: 348: temp[2]=0x50;
      008453 1E 0A            [ 2]  933 	ldw	x, (0x0a, sp)
      008455 A6 50            [ 1]  934 	ld	a, #0x50
      008457 F7               [ 1]  935 	ld	(x), a
                                    936 ;	se8r01-receive-pwm.c: 349: temp[3]=0x40;
      008458 1E 08            [ 2]  937 	ldw	x, (0x08, sp)
      00845A A6 40            [ 1]  938 	ld	a, #0x40
      00845C F7               [ 1]  939 	ld	(x), a
                                    940 ;	se8r01-receive-pwm.c: 350: temp[4]=0x50;
      00845D 1E 06            [ 2]  941 	ldw	x, (0x06, sp)
      00845F A6 50            [ 1]  942 	ld	a, #0x50
      008461 E7 04            [ 1]  943 	ld	(0x0004, x), a
                                    944 ;	se8r01-receive-pwm.c: 351: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_CAL_CTL, temp, 5);
      008463 1E 06            [ 2]  945 	ldw	x, (0x06, sp)
      008465 4B 05            [ 1]  946 	push	#0x05
      008467 89               [ 2]  947 	pushw	x
      008468 4B 23            [ 1]  948 	push	#0x23
      00846A CD 81 48         [ 4]  949 	call	_write_spi_buf
      00846D 5B 04            [ 2]  950 	addw	sp, #4
                                    951 ;	se8r01-receive-pwm.c: 353: temp[0]=0x00;
      00846F 1E 06            [ 2]  952 	ldw	x, (0x06, sp)
      008471 7F               [ 1]  953 	clr	(x)
                                    954 ;	se8r01-receive-pwm.c: 354: temp[1]=0x00;
      008472 1E 0C            [ 2]  955 	ldw	x, (0x0c, sp)
      008474 7F               [ 1]  956 	clr	(x)
                                    957 ;	se8r01-receive-pwm.c: 355: if (SE8R01_DR_2M==1)
      008475 CE 00 10         [ 2]  958 	ldw	x, _SE8R01_DR_2M+0
      008478 A3 00 01         [ 2]  959 	cpw	x, #0x0001
      00847B 26 07            [ 1]  960 	jrne	00111$
                                    961 ;	se8r01-receive-pwm.c: 356: { temp[2]=0x1E;}
      00847D 1E 0A            [ 2]  962 	ldw	x, (0x0a, sp)
      00847F A6 1E            [ 1]  963 	ld	a, #0x1e
      008481 F7               [ 1]  964 	ld	(x), a
      008482 20 05            [ 2]  965 	jra	00112$
      008484                        966 00111$:
                                    967 ;	se8r01-receive-pwm.c: 358: { temp[2]=0x1F;}
      008484 1E 0A            [ 2]  968 	ldw	x, (0x0a, sp)
      008486 A6 1F            [ 1]  969 	ld	a, #0x1f
      008488 F7               [ 1]  970 	ld	(x), a
      008489                        971 00112$:
                                    972 ;	se8r01-receive-pwm.c: 360: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_IF_FREQ, temp, 3);
      008489 1E 06            [ 2]  973 	ldw	x, (0x06, sp)
      00848B 4B 03            [ 1]  974 	push	#0x03
      00848D 89               [ 2]  975 	pushw	x
      00848E 4B 2A            [ 1]  976 	push	#0x2a
      008490 CD 81 48         [ 4]  977 	call	_write_spi_buf
      008493 5B 04            [ 2]  978 	addw	sp, #4
                                    979 ;	se8r01-receive-pwm.c: 362: if (SE8R01_DR_2M==1)
      008495 CE 00 10         [ 2]  980 	ldw	x, _SE8R01_DR_2M+0
      008498 A3 00 01         [ 2]  981 	cpw	x, #0x0001
      00849B 26 07            [ 1]  982 	jrne	00114$
                                    983 ;	se8r01-receive-pwm.c: 363: { temp[0]=0x29;}
      00849D 1E 06            [ 2]  984 	ldw	x, (0x06, sp)
      00849F A6 29            [ 1]  985 	ld	a, #0x29
      0084A1 F7               [ 1]  986 	ld	(x), a
      0084A2 20 05            [ 2]  987 	jra	00115$
      0084A4                        988 00114$:
                                    989 ;	se8r01-receive-pwm.c: 365: { temp[0]=0x14;}
      0084A4 1E 06            [ 2]  990 	ldw	x, (0x06, sp)
      0084A6 A6 14            [ 1]  991 	ld	a, #0x14
      0084A8 F7               [ 1]  992 	ld	(x), a
      0084A9                        993 00115$:
                                    994 ;	se8r01-receive-pwm.c: 367: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FDEV, temp, 1);
      0084A9 1E 06            [ 2]  995 	ldw	x, (0x06, sp)
      0084AB 4B 01            [ 1]  996 	push	#0x01
      0084AD 89               [ 2]  997 	pushw	x
      0084AE 4B 2C            [ 1]  998 	push	#0x2c
      0084B0 CD 81 48         [ 4]  999 	call	_write_spi_buf
      0084B3 5B 04            [ 2] 1000 	addw	sp, #4
                                   1001 ;	se8r01-receive-pwm.c: 369: temp[0]=0x00;
      0084B5 1E 06            [ 2] 1002 	ldw	x, (0x06, sp)
      0084B7 7F               [ 1] 1003 	clr	(x)
                                   1004 ;	se8r01-receive-pwm.c: 370: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_DAC_CAL_LOW,temp,1);
      0084B8 1E 06            [ 2] 1005 	ldw	x, (0x06, sp)
      0084BA 4B 01            [ 1] 1006 	push	#0x01
      0084BC 89               [ 2] 1007 	pushw	x
      0084BD 4B 37            [ 1] 1008 	push	#0x37
      0084BF CD 81 48         [ 4] 1009 	call	_write_spi_buf
      0084C2 5B 04            [ 2] 1010 	addw	sp, #4
                                   1011 ;	se8r01-receive-pwm.c: 372: temp[0]=0x7F;
      0084C4 1E 06            [ 2] 1012 	ldw	x, (0x06, sp)
      0084C6 A6 7F            [ 1] 1013 	ld	a, #0x7f
      0084C8 F7               [ 1] 1014 	ld	(x), a
                                   1015 ;	se8r01-receive-pwm.c: 373: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_DAC_CAL_HI,temp,1);
      0084C9 1E 06            [ 2] 1016 	ldw	x, (0x06, sp)
      0084CB 4B 01            [ 1] 1017 	push	#0x01
      0084CD 89               [ 2] 1018 	pushw	x
      0084CE 4B 38            [ 1] 1019 	push	#0x38
      0084D0 CD 81 48         [ 4] 1020 	call	_write_spi_buf
      0084D3 5B 04            [ 2] 1021 	addw	sp, #4
                                   1022 ;	se8r01-receive-pwm.c: 375: temp[0]=0x02;
      0084D5 1E 06            [ 2] 1023 	ldw	x, (0x06, sp)
      0084D7 A6 02            [ 1] 1024 	ld	a, #0x02
      0084D9 F7               [ 1] 1025 	ld	(x), a
                                   1026 ;	se8r01-receive-pwm.c: 376: temp[1]=0xC1;
      0084DA 1E 0C            [ 2] 1027 	ldw	x, (0x0c, sp)
      0084DC A6 C1            [ 1] 1028 	ld	a, #0xc1
      0084DE F7               [ 1] 1029 	ld	(x), a
                                   1030 ;	se8r01-receive-pwm.c: 377: temp[2]=0xEB;            
      0084DF 1E 0A            [ 2] 1031 	ldw	x, (0x0a, sp)
      0084E1 A6 EB            [ 1] 1032 	ld	a, #0xeb
      0084E3 F7               [ 1] 1033 	ld	(x), a
                                   1034 ;	se8r01-receive-pwm.c: 378: temp[3]=0x1C;
      0084E4 1E 08            [ 2] 1035 	ldw	x, (0x08, sp)
      0084E6 A6 1C            [ 1] 1036 	ld	a, #0x1c
      0084E8 F7               [ 1] 1037 	ld	(x), a
                                   1038 ;	se8r01-receive-pwm.c: 379: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_AGC_GAIN, temp,4);
      0084E9 1E 06            [ 2] 1039 	ldw	x, (0x06, sp)
      0084EB 4B 04            [ 1] 1040 	push	#0x04
      0084ED 89               [ 2] 1041 	pushw	x
      0084EE 4B 3D            [ 1] 1042 	push	#0x3d
      0084F0 CD 81 48         [ 4] 1043 	call	_write_spi_buf
      0084F3 5B 04            [ 2] 1044 	addw	sp, #4
                                   1045 ;	se8r01-receive-pwm.c: 381: temp[0]=0x97;
      0084F5 1E 06            [ 2] 1046 	ldw	x, (0x06, sp)
      0084F7 A6 97            [ 1] 1047 	ld	a, #0x97
      0084F9 F7               [ 1] 1048 	ld	(x), a
                                   1049 ;	se8r01-receive-pwm.c: 382: temp[1]=0x64;
      0084FA 1E 0C            [ 2] 1050 	ldw	x, (0x0c, sp)
      0084FC A6 64            [ 1] 1051 	ld	a, #0x64
      0084FE F7               [ 1] 1052 	ld	(x), a
                                   1053 ;	se8r01-receive-pwm.c: 383: temp[2]=0x00;
      0084FF 1E 0A            [ 2] 1054 	ldw	x, (0x0a, sp)
      008501 7F               [ 1] 1055 	clr	(x)
                                   1056 ;	se8r01-receive-pwm.c: 384: temp[3]=0x81;
      008502 1E 08            [ 2] 1057 	ldw	x, (0x08, sp)
      008504 A6 81            [ 1] 1058 	ld	a, #0x81
      008506 F7               [ 1] 1059 	ld	(x), a
                                   1060 ;	se8r01-receive-pwm.c: 385: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RF_IVGEN, temp, 4);
      008507 1E 06            [ 2] 1061 	ldw	x, (0x06, sp)
      008509 4B 04            [ 1] 1062 	push	#0x04
      00850B 89               [ 2] 1063 	pushw	x
      00850C 4B 3E            [ 1] 1064 	push	#0x3e
      00850E CD 81 48         [ 4] 1065 	call	_write_spi_buf
      008511 5B 04            [ 2] 1066 	addw	sp, #4
                                   1067 ;	se8r01-receive-pwm.c: 386: rf_switch_bank(iBANK0);
      008513 4B 00            [ 1] 1068 	push	#0x00
      008515 CD 83 79         [ 4] 1069 	call	_rf_switch_bank
      008518 84               [ 1] 1070 	pop	a
                                   1071 ;	se8r01-receive-pwm.c: 391: delayTenMicro();
      008519 CD 80 A0         [ 4] 1072 	call	_delayTenMicro
                                   1073 ;	se8r01-receive-pwm.c: 392: PC_ODR |= (1 << CE);
      00851C AE 50 0A         [ 2] 1074 	ldw	x, #0x500a
      00851F F6               [ 1] 1075 	ld	a, (x)
      008520 AA 10            [ 1] 1076 	or	a, #0x10
      008522 F7               [ 1] 1077 	ld	(x), a
                                   1078 ;	se8r01-receive-pwm.c: 393: delayTenMicro();
      008523 CD 80 A0         [ 4] 1079 	call	_delayTenMicro
                                   1080 ;	se8r01-receive-pwm.c: 394: delayTenMicro();
      008526 CD 80 A0         [ 4] 1081 	call	_delayTenMicro
                                   1082 ;	se8r01-receive-pwm.c: 395: delayTenMicro();
      008529 CD 80 A0         [ 4] 1083 	call	_delayTenMicro
                                   1084 ;	se8r01-receive-pwm.c: 396: PC_ODR &= ~(1 << CE);
      00852C AE 50 0A         [ 2] 1085 	ldw	x, #0x500a
      00852F F6               [ 1] 1086 	ld	a, (x)
      008530 A4 EF            [ 1] 1087 	and	a, #0xef
      008532 F7               [ 1] 1088 	ld	(x), a
                                   1089 ;	se8r01-receive-pwm.c: 397: delay(50);                            // delay 50ms waitting for calibaration.
      008533 4B 32            [ 1] 1090 	push	#0x32
      008535 4B 00            [ 1] 1091 	push	#0x00
      008537 CD 82 2E         [ 4] 1092 	call	_delay
      00853A 5B 02            [ 2] 1093 	addw	sp, #2
                                   1094 ;	se8r01-receive-pwm.c: 402: delayTenMicro();
      00853C CD 80 A0         [ 4] 1095 	call	_delayTenMicro
                                   1096 ;	se8r01-receive-pwm.c: 403: PC_ODR |= (1 << CE);
      00853F AE 50 0A         [ 2] 1097 	ldw	x, #0x500a
      008542 F6               [ 1] 1098 	ld	a, (x)
      008543 AA 10            [ 1] 1099 	or	a, #0x10
      008545 F7               [ 1] 1100 	ld	(x), a
                                   1101 ;	se8r01-receive-pwm.c: 404: delayTenMicro();
      008546 CD 80 A0         [ 4] 1102 	call	_delayTenMicro
                                   1103 ;	se8r01-receive-pwm.c: 405: delayTenMicro();
      008549 CD 80 A0         [ 4] 1104 	call	_delayTenMicro
                                   1105 ;	se8r01-receive-pwm.c: 406: delayTenMicro();
      00854C CD 80 A0         [ 4] 1106 	call	_delayTenMicro
                                   1107 ;	se8r01-receive-pwm.c: 407: PC_ODR &= ~(1 << CE);
      00854F AE 50 0A         [ 2] 1108 	ldw	x, #0x500a
      008552 F6               [ 1] 1109 	ld	a, (x)
      008553 A4 EF            [ 1] 1110 	and	a, #0xef
      008555 F7               [ 1] 1111 	ld	(x), a
                                   1112 ;	se8r01-receive-pwm.c: 408: delay(50);                            // delay 50ms waitting for calibaration.
      008556 4B 32            [ 1] 1113 	push	#0x32
      008558 4B 00            [ 1] 1114 	push	#0x00
      00855A CD 82 2E         [ 4] 1115 	call	_delay
      00855D 5B 02            [ 2] 1116 	addw	sp, #2
      00855F 5B 0D            [ 2] 1117 	addw	sp, #13
      008561 81               [ 4] 1118 	ret
                                   1119 ;	se8r01-receive-pwm.c: 412: void SE8R01_Analog_Init()           //SE8R01 初始化
                                   1120 ;	-----------------------------------------
                                   1121 ;	 function SE8R01_Analog_Init
                                   1122 ;	-----------------------------------------
      008562                       1123 _SE8R01_Analog_Init:
      008562 52 15            [ 2] 1124 	sub	sp, #21
                                   1125 ;	se8r01-receive-pwm.c: 417: gtemp[0]=0x28;
      008564 AE 00 01         [ 2] 1126 	ldw	x, #_gtemp+0
      008567 1F 14            [ 2] 1127 	ldw	(0x14, sp), x
      008569 1E 14            [ 2] 1128 	ldw	x, (0x14, sp)
      00856B A6 28            [ 1] 1129 	ld	a, #0x28
      00856D F7               [ 1] 1130 	ld	(x), a
                                   1131 ;	se8r01-receive-pwm.c: 418: gtemp[1]=0x32;
      00856E 1E 14            [ 2] 1132 	ldw	x, (0x14, sp)
      008570 5C               [ 2] 1133 	incw	x
      008571 1F 08            [ 2] 1134 	ldw	(0x08, sp), x
      008573 1E 08            [ 2] 1135 	ldw	x, (0x08, sp)
      008575 A6 32            [ 1] 1136 	ld	a, #0x32
      008577 F7               [ 1] 1137 	ld	(x), a
                                   1138 ;	se8r01-receive-pwm.c: 419: gtemp[2]=0x80;
      008578 1E 14            [ 2] 1139 	ldw	x, (0x14, sp)
      00857A 5C               [ 2] 1140 	incw	x
      00857B 5C               [ 2] 1141 	incw	x
      00857C 1F 06            [ 2] 1142 	ldw	(0x06, sp), x
      00857E 1E 06            [ 2] 1143 	ldw	x, (0x06, sp)
      008580 A6 80            [ 1] 1144 	ld	a, #0x80
      008582 F7               [ 1] 1145 	ld	(x), a
                                   1146 ;	se8r01-receive-pwm.c: 420: gtemp[3]=0x90;
      008583 1E 14            [ 2] 1147 	ldw	x, (0x14, sp)
      008585 1C 00 03         [ 2] 1148 	addw	x, #0x0003
      008588 1F 0E            [ 2] 1149 	ldw	(0x0e, sp), x
      00858A 1E 0E            [ 2] 1150 	ldw	x, (0x0e, sp)
      00858C A6 90            [ 1] 1151 	ld	a, #0x90
      00858E F7               [ 1] 1152 	ld	(x), a
                                   1153 ;	se8r01-receive-pwm.c: 421: gtemp[4]=0x00;
      00858F 1E 14            [ 2] 1154 	ldw	x, (0x14, sp)
      008591 1C 00 04         [ 2] 1155 	addw	x, #0x0004
      008594 7F               [ 1] 1156 	clr	(x)
                                   1157 ;	se8r01-receive-pwm.c: 422: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_SETUP_VALUE, gtemp, 5);
      008595 1E 14            [ 2] 1158 	ldw	x, (0x14, sp)
      008597 4B 05            [ 1] 1159 	push	#0x05
      008599 89               [ 2] 1160 	pushw	x
      00859A 4B 3E            [ 1] 1161 	push	#0x3e
      00859C CD 81 48         [ 4] 1162 	call	_write_spi_buf
      00859F 5B 04            [ 2] 1163 	addw	sp, #4
                                   1164 ;	se8r01-receive-pwm.c: 423: delay(2);
      0085A1 4B 02            [ 1] 1165 	push	#0x02
      0085A3 4B 00            [ 1] 1166 	push	#0x00
      0085A5 CD 82 2E         [ 4] 1167 	call	_delay
      0085A8 5B 02            [ 2] 1168 	addw	sp, #2
                                   1169 ;	se8r01-receive-pwm.c: 426: rf_switch_bank(iBANK1);
      0085AA 4B 80            [ 1] 1170 	push	#0x80
      0085AC CD 83 79         [ 4] 1171 	call	_rf_switch_bank
      0085AF 84               [ 1] 1172 	pop	a
                                   1173 ;	se8r01-receive-pwm.c: 428: temp[0]=0x40;
      0085B0 96               [ 1] 1174 	ldw	x, sp
      0085B1 5C               [ 2] 1175 	incw	x
      0085B2 1F 0C            [ 2] 1176 	ldw	(0x0c, sp), x
      0085B4 1E 0C            [ 2] 1177 	ldw	x, (0x0c, sp)
      0085B6 A6 40            [ 1] 1178 	ld	a, #0x40
      0085B8 F7               [ 1] 1179 	ld	(x), a
                                   1180 ;	se8r01-receive-pwm.c: 429: temp[1]=0x01;               
      0085B9 1E 0C            [ 2] 1181 	ldw	x, (0x0c, sp)
      0085BB 5C               [ 2] 1182 	incw	x
      0085BC 1F 0A            [ 2] 1183 	ldw	(0x0a, sp), x
      0085BE 1E 0A            [ 2] 1184 	ldw	x, (0x0a, sp)
      0085C0 A6 01            [ 1] 1185 	ld	a, #0x01
      0085C2 F7               [ 1] 1186 	ld	(x), a
                                   1187 ;	se8r01-receive-pwm.c: 430: temp[2]=0x30;               
      0085C3 1E 0C            [ 2] 1188 	ldw	x, (0x0c, sp)
      0085C5 5C               [ 2] 1189 	incw	x
      0085C6 5C               [ 2] 1190 	incw	x
      0085C7 1F 12            [ 2] 1191 	ldw	(0x12, sp), x
      0085C9 1E 12            [ 2] 1192 	ldw	x, (0x12, sp)
      0085CB A6 30            [ 1] 1193 	ld	a, #0x30
      0085CD F7               [ 1] 1194 	ld	(x), a
                                   1195 ;	se8r01-receive-pwm.c: 432: { temp[3]=0xE2; }              
      0085CE 1E 0C            [ 2] 1196 	ldw	x, (0x0c, sp)
      0085D0 1C 00 03         [ 2] 1197 	addw	x, #0x0003
      0085D3 1F 10            [ 2] 1198 	ldw	(0x10, sp), x
                                   1199 ;	se8r01-receive-pwm.c: 431: if (SE8R01_DR_2M==1)
      0085D5 CE 00 10         [ 2] 1200 	ldw	x, _SE8R01_DR_2M+0
      0085D8 A3 00 01         [ 2] 1201 	cpw	x, #0x0001
      0085DB 26 07            [ 1] 1202 	jrne	00102$
                                   1203 ;	se8r01-receive-pwm.c: 432: { temp[3]=0xE2; }              
      0085DD 1E 10            [ 2] 1204 	ldw	x, (0x10, sp)
      0085DF A6 E2            [ 1] 1205 	ld	a, #0xe2
      0085E1 F7               [ 1] 1206 	ld	(x), a
      0085E2 20 05            [ 2] 1207 	jra	00103$
      0085E4                       1208 00102$:
                                   1209 ;	se8r01-receive-pwm.c: 434: { temp[3]=0xE0;}
      0085E4 1E 10            [ 2] 1210 	ldw	x, (0x10, sp)
      0085E6 A6 E0            [ 1] 1211 	ld	a, #0xe0
      0085E8 F7               [ 1] 1212 	ld	(x), a
      0085E9                       1213 00103$:
                                   1214 ;	se8r01-receive-pwm.c: 436: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_PLL_CTL0, temp,4);
      0085E9 1E 0C            [ 2] 1215 	ldw	x, (0x0c, sp)
      0085EB 4B 04            [ 1] 1216 	push	#0x04
      0085ED 89               [ 2] 1217 	pushw	x
      0085EE 4B 21            [ 1] 1218 	push	#0x21
      0085F0 CD 81 48         [ 4] 1219 	call	_write_spi_buf
      0085F3 5B 04            [ 2] 1220 	addw	sp, #4
                                   1221 ;	se8r01-receive-pwm.c: 438: temp[0]=0x29;
      0085F5 1E 0C            [ 2] 1222 	ldw	x, (0x0c, sp)
      0085F7 A6 29            [ 1] 1223 	ld	a, #0x29
      0085F9 F7               [ 1] 1224 	ld	(x), a
                                   1225 ;	se8r01-receive-pwm.c: 439: temp[1]=0x89;
      0085FA 1E 0A            [ 2] 1226 	ldw	x, (0x0a, sp)
      0085FC A6 89            [ 1] 1227 	ld	a, #0x89
      0085FE F7               [ 1] 1228 	ld	(x), a
                                   1229 ;	se8r01-receive-pwm.c: 440: temp[2]=0x55;                     
      0085FF 1E 12            [ 2] 1230 	ldw	x, (0x12, sp)
      008601 A6 55            [ 1] 1231 	ld	a, #0x55
      008603 F7               [ 1] 1232 	ld	(x), a
                                   1233 ;	se8r01-receive-pwm.c: 441: temp[3]=0x40;
      008604 1E 10            [ 2] 1234 	ldw	x, (0x10, sp)
      008606 A6 40            [ 1] 1235 	ld	a, #0x40
      008608 F7               [ 1] 1236 	ld	(x), a
                                   1237 ;	se8r01-receive-pwm.c: 442: temp[4]=0x50;
      008609 1E 0C            [ 2] 1238 	ldw	x, (0x0c, sp)
      00860B A6 50            [ 1] 1239 	ld	a, #0x50
      00860D E7 04            [ 1] 1240 	ld	(0x0004, x), a
                                   1241 ;	se8r01-receive-pwm.c: 443: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_CAL_CTL, temp,5);
      00860F 1E 0C            [ 2] 1242 	ldw	x, (0x0c, sp)
      008611 4B 05            [ 1] 1243 	push	#0x05
      008613 89               [ 2] 1244 	pushw	x
      008614 4B 23            [ 1] 1245 	push	#0x23
      008616 CD 81 48         [ 4] 1246 	call	_write_spi_buf
      008619 5B 04            [ 2] 1247 	addw	sp, #4
                                   1248 ;	se8r01-receive-pwm.c: 445: if (SE8R01_DR_2M==1)
      00861B CE 00 10         [ 2] 1249 	ldw	x, _SE8R01_DR_2M+0
      00861E A3 00 01         [ 2] 1250 	cpw	x, #0x0001
      008621 26 07            [ 1] 1251 	jrne	00105$
                                   1252 ;	se8r01-receive-pwm.c: 446: { temp[0]=0x29;}
      008623 1E 0C            [ 2] 1253 	ldw	x, (0x0c, sp)
      008625 A6 29            [ 1] 1254 	ld	a, #0x29
      008627 F7               [ 1] 1255 	ld	(x), a
      008628 20 05            [ 2] 1256 	jra	00106$
      00862A                       1257 00105$:
                                   1258 ;	se8r01-receive-pwm.c: 448: { temp[0]=0x14;}
      00862A 1E 0C            [ 2] 1259 	ldw	x, (0x0c, sp)
      00862C A6 14            [ 1] 1260 	ld	a, #0x14
      00862E F7               [ 1] 1261 	ld	(x), a
      00862F                       1262 00106$:
                                   1263 ;	se8r01-receive-pwm.c: 450: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FDEV, temp,1);
      00862F 1E 0C            [ 2] 1264 	ldw	x, (0x0c, sp)
      008631 4B 01            [ 1] 1265 	push	#0x01
      008633 89               [ 2] 1266 	pushw	x
      008634 4B 2C            [ 1] 1267 	push	#0x2c
      008636 CD 81 48         [ 4] 1268 	call	_write_spi_buf
      008639 5B 04            [ 2] 1269 	addw	sp, #4
                                   1270 ;	se8r01-receive-pwm.c: 452: temp[0]=0x55;
      00863B 1E 0C            [ 2] 1271 	ldw	x, (0x0c, sp)
      00863D A6 55            [ 1] 1272 	ld	a, #0x55
      00863F F7               [ 1] 1273 	ld	(x), a
                                   1274 ;	se8r01-receive-pwm.c: 453: temp[1]=0xC2;
      008640 1E 0A            [ 2] 1275 	ldw	x, (0x0a, sp)
      008642 A6 C2            [ 1] 1276 	ld	a, #0xc2
      008644 F7               [ 1] 1277 	ld	(x), a
                                   1278 ;	se8r01-receive-pwm.c: 454: temp[2]=0x09;
      008645 1E 12            [ 2] 1279 	ldw	x, (0x12, sp)
      008647 A6 09            [ 1] 1280 	ld	a, #0x09
      008649 F7               [ 1] 1281 	ld	(x), a
                                   1282 ;	se8r01-receive-pwm.c: 455: temp[3]=0xAC;  
      00864A 1E 10            [ 2] 1283 	ldw	x, (0x10, sp)
      00864C A6 AC            [ 1] 1284 	ld	a, #0xac
      00864E F7               [ 1] 1285 	ld	(x), a
                                   1286 ;	se8r01-receive-pwm.c: 456: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RX_CTRL,temp,4);
      00864F 1E 0C            [ 2] 1287 	ldw	x, (0x0c, sp)
      008651 4B 04            [ 1] 1288 	push	#0x04
      008653 89               [ 2] 1289 	pushw	x
      008654 4B 31            [ 1] 1290 	push	#0x31
      008656 CD 81 48         [ 4] 1291 	call	_write_spi_buf
      008659 5B 04            [ 2] 1292 	addw	sp, #4
                                   1293 ;	se8r01-receive-pwm.c: 458: temp[0]=0x00;
      00865B 1E 0C            [ 2] 1294 	ldw	x, (0x0c, sp)
      00865D 7F               [ 1] 1295 	clr	(x)
                                   1296 ;	se8r01-receive-pwm.c: 459: temp[1]=0x14;
      00865E 1E 0A            [ 2] 1297 	ldw	x, (0x0a, sp)
      008660 A6 14            [ 1] 1298 	ld	a, #0x14
      008662 F7               [ 1] 1299 	ld	(x), a
                                   1300 ;	se8r01-receive-pwm.c: 460: temp[2]=0x08;   
      008663 1E 12            [ 2] 1301 	ldw	x, (0x12, sp)
      008665 A6 08            [ 1] 1302 	ld	a, #0x08
      008667 F7               [ 1] 1303 	ld	(x), a
                                   1304 ;	se8r01-receive-pwm.c: 461: temp[3]=0x29;
      008668 1E 10            [ 2] 1305 	ldw	x, (0x10, sp)
      00866A A6 29            [ 1] 1306 	ld	a, #0x29
      00866C F7               [ 1] 1307 	ld	(x), a
                                   1308 ;	se8r01-receive-pwm.c: 462: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_FAGC_CTRL_1, temp,4);
      00866D 1E 0C            [ 2] 1309 	ldw	x, (0x0c, sp)
      00866F 4B 04            [ 1] 1310 	push	#0x04
      008671 89               [ 2] 1311 	pushw	x
      008672 4B 33            [ 1] 1312 	push	#0x33
      008674 CD 81 48         [ 4] 1313 	call	_write_spi_buf
      008677 5B 04            [ 2] 1314 	addw	sp, #4
                                   1315 ;	se8r01-receive-pwm.c: 464: temp[0]=0x02;
      008679 1E 0C            [ 2] 1316 	ldw	x, (0x0c, sp)
      00867B A6 02            [ 1] 1317 	ld	a, #0x02
      00867D F7               [ 1] 1318 	ld	(x), a
                                   1319 ;	se8r01-receive-pwm.c: 465: temp[1]=0xC1;
      00867E 1E 0A            [ 2] 1320 	ldw	x, (0x0a, sp)
      008680 A6 C1            [ 1] 1321 	ld	a, #0xc1
      008682 F7               [ 1] 1322 	ld	(x), a
                                   1323 ;	se8r01-receive-pwm.c: 466: temp[2]=0xCB;  
      008683 1E 12            [ 2] 1324 	ldw	x, (0x12, sp)
      008685 A6 CB            [ 1] 1325 	ld	a, #0xcb
      008687 F7               [ 1] 1326 	ld	(x), a
                                   1327 ;	se8r01-receive-pwm.c: 467: temp[3]=0x1C;
      008688 1E 10            [ 2] 1328 	ldw	x, (0x10, sp)
      00868A A6 1C            [ 1] 1329 	ld	a, #0x1c
      00868C F7               [ 1] 1330 	ld	(x), a
                                   1331 ;	se8r01-receive-pwm.c: 468: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_AGC_GAIN, temp,4);
      00868D 1E 0C            [ 2] 1332 	ldw	x, (0x0c, sp)
      00868F 4B 04            [ 1] 1333 	push	#0x04
      008691 89               [ 2] 1334 	pushw	x
      008692 4B 3D            [ 1] 1335 	push	#0x3d
      008694 CD 81 48         [ 4] 1336 	call	_write_spi_buf
      008697 5B 04            [ 2] 1337 	addw	sp, #4
                                   1338 ;	se8r01-receive-pwm.c: 470: temp[0]=0x97;
      008699 1E 0C            [ 2] 1339 	ldw	x, (0x0c, sp)
      00869B A6 97            [ 1] 1340 	ld	a, #0x97
      00869D F7               [ 1] 1341 	ld	(x), a
                                   1342 ;	se8r01-receive-pwm.c: 471: temp[1]=0x64;
      00869E 1E 0A            [ 2] 1343 	ldw	x, (0x0a, sp)
      0086A0 A6 64            [ 1] 1344 	ld	a, #0x64
      0086A2 F7               [ 1] 1345 	ld	(x), a
                                   1346 ;	se8r01-receive-pwm.c: 472: temp[2]=0x00;
      0086A3 1E 12            [ 2] 1347 	ldw	x, (0x12, sp)
      0086A5 7F               [ 1] 1348 	clr	(x)
                                   1349 ;	se8r01-receive-pwm.c: 473: temp[3]=0x01;
      0086A6 1E 10            [ 2] 1350 	ldw	x, (0x10, sp)
      0086A8 A6 01            [ 1] 1351 	ld	a, #0x01
      0086AA F7               [ 1] 1352 	ld	(x), a
                                   1353 ;	se8r01-receive-pwm.c: 474: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_RF_IVGEN, temp,4);
      0086AB 1E 0C            [ 2] 1354 	ldw	x, (0x0c, sp)
      0086AD 4B 04            [ 1] 1355 	push	#0x04
      0086AF 89               [ 2] 1356 	pushw	x
      0086B0 4B 3E            [ 1] 1357 	push	#0x3e
      0086B2 CD 81 48         [ 4] 1358 	call	_write_spi_buf
      0086B5 5B 04            [ 2] 1359 	addw	sp, #4
                                   1360 ;	se8r01-receive-pwm.c: 476: gtemp[0]=0x2A;
      0086B7 1E 14            [ 2] 1361 	ldw	x, (0x14, sp)
      0086B9 A6 2A            [ 1] 1362 	ld	a, #0x2a
      0086BB F7               [ 1] 1363 	ld	(x), a
                                   1364 ;	se8r01-receive-pwm.c: 477: gtemp[1]=0x04;
      0086BC 1E 08            [ 2] 1365 	ldw	x, (0x08, sp)
      0086BE A6 04            [ 1] 1366 	ld	a, #0x04
      0086C0 F7               [ 1] 1367 	ld	(x), a
                                   1368 ;	se8r01-receive-pwm.c: 478: gtemp[2]=0x00;
      0086C1 1E 06            [ 2] 1369 	ldw	x, (0x06, sp)
      0086C3 7F               [ 1] 1370 	clr	(x)
                                   1371 ;	se8r01-receive-pwm.c: 479: gtemp[3]=0x7D;
      0086C4 1E 0E            [ 2] 1372 	ldw	x, (0x0e, sp)
      0086C6 A6 7D            [ 1] 1373 	ld	a, #0x7d
      0086C8 F7               [ 1] 1374 	ld	(x), a
                                   1375 ;	se8r01-receive-pwm.c: 480: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK1_TEST_PKDET, gtemp, 4);
      0086C9 1E 14            [ 2] 1376 	ldw	x, (0x14, sp)
      0086CB 4B 04            [ 1] 1377 	push	#0x04
      0086CD 89               [ 2] 1378 	pushw	x
      0086CE 4B 3F            [ 1] 1379 	push	#0x3f
      0086D0 CD 81 48         [ 4] 1380 	call	_write_spi_buf
      0086D3 5B 04            [ 2] 1381 	addw	sp, #4
                                   1382 ;	se8r01-receive-pwm.c: 482: rf_switch_bank(iBANK0);
      0086D5 4B 00            [ 1] 1383 	push	#0x00
      0086D7 CD 83 79         [ 4] 1384 	call	_rf_switch_bank
      0086DA 84               [ 1] 1385 	pop	a
      0086DB 5B 15            [ 2] 1386 	addw	sp, #21
      0086DD 81               [ 4] 1387 	ret
                                   1388 ;	se8r01-receive-pwm.c: 485: void SE8R01_Init()  
                                   1389 ;	-----------------------------------------
                                   1390 ;	 function SE8R01_Init
                                   1391 ;	-----------------------------------------
      0086DE                       1392 _SE8R01_Init:
      0086DE 52 05            [ 2] 1393 	sub	sp, #5
                                   1394 ;	se8r01-receive-pwm.c: 488: SE8R01_Calibration();   
      0086E0 CD 83 96         [ 4] 1395 	call	_SE8R01_Calibration
                                   1396 ;	se8r01-receive-pwm.c: 489: SE8R01_Analog_Init();   
      0086E3 CD 85 62         [ 4] 1397 	call	_SE8R01_Analog_Init
                                   1398 ;	se8r01-receive-pwm.c: 493: if (SE8R01_DR_2M==1)
      0086E6 CE 00 10         [ 2] 1399 	ldw	x, _SE8R01_DR_2M+0
      0086E9 A3 00 01         [ 2] 1400 	cpw	x, #0x0001
      0086EC 26 07            [ 1] 1401 	jrne	00105$
                                   1402 ;	se8r01-receive-pwm.c: 494: {  temp[0]=0b01001111; }     //2MHz,+5dbm
      0086EE 96               [ 1] 1403 	ldw	x, sp
      0086EF 5C               [ 2] 1404 	incw	x
      0086F0 A6 4F            [ 1] 1405 	ld	a, #0x4f
      0086F2 F7               [ 1] 1406 	ld	(x), a
      0086F3 20 14            [ 2] 1407 	jra	00106$
      0086F5                       1408 00105$:
                                   1409 ;	se8r01-receive-pwm.c: 495: else if  (SE8R01_DR_1M==1)
      0086F5 CE 00 12         [ 2] 1410 	ldw	x, _SE8R01_DR_1M+0
      0086F8 A3 00 01         [ 2] 1411 	cpw	x, #0x0001
      0086FB 26 07            [ 1] 1412 	jrne	00102$
                                   1413 ;	se8r01-receive-pwm.c: 496: {  temp[0]=0b01000111;  }     //1MHz,+5dbm
      0086FD 96               [ 1] 1414 	ldw	x, sp
      0086FE 5C               [ 2] 1415 	incw	x
      0086FF A6 47            [ 1] 1416 	ld	a, #0x47
      008701 F7               [ 1] 1417 	ld	(x), a
      008702 20 05            [ 2] 1418 	jra	00106$
      008704                       1419 00102$:
                                   1420 ;	se8r01-receive-pwm.c: 498: {temp[0]=0b01101111;  }     //500K,+5dbm
      008704 96               [ 1] 1421 	ldw	x, sp
      008705 5C               [ 2] 1422 	incw	x
      008706 A6 6F            [ 1] 1423 	ld	a, #0x6f
      008708 F7               [ 1] 1424 	ld	(x), a
      008709                       1425 00106$:
                                   1426 ;	se8r01-receive-pwm.c: 500: write_spi_buf(iRF_CMD_WRITE_REG|iRF_BANK0_RF_SETUP,temp,1);
      008709 96               [ 1] 1427 	ldw	x, sp
      00870A 5C               [ 2] 1428 	incw	x
      00870B 4B 01            [ 1] 1429 	push	#0x01
      00870D 89               [ 2] 1430 	pushw	x
      00870E 4B 26            [ 1] 1431 	push	#0x26
      008710 CD 81 48         [ 4] 1432 	call	_write_spi_buf
      008713 5B 04            [ 2] 1433 	addw	sp, #4
                                   1434 ;	se8r01-receive-pwm.c: 501: write_spi_reg(WRITE_REG|iRF_BANK0_EN_AA, 0b00111111);          //enable auto acc on pip 1
      008715 4B 3F            [ 1] 1435 	push	#0x3f
      008717 4B 21            [ 1] 1436 	push	#0x21
      008719 CD 80 CE         [ 4] 1437 	call	_write_spi_reg
      00871C 5B 02            [ 2] 1438 	addw	sp, #2
                                   1439 ;	se8r01-receive-pwm.c: 502: write_spi_reg(WRITE_REG|iRF_BANK0_EN_RXADDR, 0b00111111);      //enable pip 1
      00871E 4B 3F            [ 1] 1440 	push	#0x3f
      008720 4B 22            [ 1] 1441 	push	#0x22
      008722 CD 80 CE         [ 4] 1442 	call	_write_spi_reg
      008725 5B 02            [ 2] 1443 	addw	sp, #2
                                   1444 ;	se8r01-receive-pwm.c: 503: write_spi_reg(WRITE_REG|iRF_BANK0_SETUP_AW, 0x02);  
      008727 4B 02            [ 1] 1445 	push	#0x02
      008729 4B 23            [ 1] 1446 	push	#0x23
      00872B CD 80 CE         [ 4] 1447 	call	_write_spi_reg
      00872E 5B 02            [ 2] 1448 	addw	sp, #2
                                   1449 ;	se8r01-receive-pwm.c: 504: write_spi_reg(WRITE_REG|iRF_BANK0_RF_CH, 40);
      008730 4B 28            [ 1] 1450 	push	#0x28
      008732 4B 25            [ 1] 1451 	push	#0x25
      008734 CD 80 CE         [ 4] 1452 	call	_write_spi_reg
      008737 5B 02            [ 2] 1453 	addw	sp, #2
                                   1454 ;	se8r01-receive-pwm.c: 506: write_spi_buf(WRITE_REG + TX_ADDR, ADDRESS0, ADR_WIDTH);    	
      008739 AE 00 2A         [ 2] 1455 	ldw	x, #_ADDRESS0+0
      00873C 90 93            [ 1] 1456 	ldw	y, x
      00873E 89               [ 2] 1457 	pushw	x
      00873F 4B 04            [ 1] 1458 	push	#0x04
      008741 90 89            [ 2] 1459 	pushw	y
      008743 4B 30            [ 1] 1460 	push	#0x30
      008745 CD 81 48         [ 4] 1461 	call	_write_spi_buf
      008748 5B 04            [ 2] 1462 	addw	sp, #4
      00874A 85               [ 2] 1463 	popw	x
                                   1464 ;	se8r01-receive-pwm.c: 507: write_spi_buf(WRITE_REG + RX_ADDR_P0, ADDRESS0, ADR_WIDTH); 
      00874B 4B 04            [ 1] 1465 	push	#0x04
      00874D 89               [ 2] 1466 	pushw	x
      00874E 4B 2A            [ 1] 1467 	push	#0x2a
      008750 CD 81 48         [ 4] 1468 	call	_write_spi_buf
      008753 5B 04            [ 2] 1469 	addw	sp, #4
                                   1470 ;	se8r01-receive-pwm.c: 508: write_spi_buf(WRITE_REG + RX_ADDR_P1, ADDRESS1, ADR_WIDTH); 
      008755 AE 00 26         [ 2] 1471 	ldw	x, #_ADDRESS1+0
      008758 4B 04            [ 1] 1472 	push	#0x04
      00875A 89               [ 2] 1473 	pushw	x
      00875B 4B 2B            [ 1] 1474 	push	#0x2b
      00875D CD 81 48         [ 4] 1475 	call	_write_spi_buf
      008760 5B 04            [ 2] 1476 	addw	sp, #4
                                   1477 ;	se8r01-receive-pwm.c: 509: write_spi_buf(WRITE_REG + RX_ADDR_P2, ADDRESS2, 1); 
      008762 AE 00 22         [ 2] 1478 	ldw	x, #_ADDRESS2+0
      008765 4B 01            [ 1] 1479 	push	#0x01
      008767 89               [ 2] 1480 	pushw	x
      008768 4B 2C            [ 1] 1481 	push	#0x2c
      00876A CD 81 48         [ 4] 1482 	call	_write_spi_buf
      00876D 5B 04            [ 2] 1483 	addw	sp, #4
                                   1484 ;	se8r01-receive-pwm.c: 510: write_spi_buf(WRITE_REG + RX_ADDR_P3, ADDRESS3, 1); 
      00876F AE 00 23         [ 2] 1485 	ldw	x, #_ADDRESS3+0
      008772 4B 01            [ 1] 1486 	push	#0x01
      008774 89               [ 2] 1487 	pushw	x
      008775 4B 2D            [ 1] 1488 	push	#0x2d
      008777 CD 81 48         [ 4] 1489 	call	_write_spi_buf
      00877A 5B 04            [ 2] 1490 	addw	sp, #4
                                   1491 ;	se8r01-receive-pwm.c: 511: write_spi_buf(WRITE_REG + RX_ADDR_P4, ADDRESS4, 1); 
      00877C AE 00 24         [ 2] 1492 	ldw	x, #_ADDRESS4+0
      00877F 4B 01            [ 1] 1493 	push	#0x01
      008781 89               [ 2] 1494 	pushw	x
      008782 4B 2E            [ 1] 1495 	push	#0x2e
      008784 CD 81 48         [ 4] 1496 	call	_write_spi_buf
      008787 5B 04            [ 2] 1497 	addw	sp, #4
                                   1498 ;	se8r01-receive-pwm.c: 512: write_spi_buf(WRITE_REG + RX_ADDR_P5, ADDRESS5, 1); 
      008789 AE 00 25         [ 2] 1499 	ldw	x, #_ADDRESS5+0
      00878C 4B 01            [ 1] 1500 	push	#0x01
      00878E 89               [ 2] 1501 	pushw	x
      00878F 4B 2F            [ 1] 1502 	push	#0x2f
      008791 CD 81 48         [ 4] 1503 	call	_write_spi_buf
      008794 5B 04            [ 2] 1504 	addw	sp, #4
                                   1505 ;	se8r01-receive-pwm.c: 513: write_spi_reg(WRITE_REG + RX_PW_P0, PLOAD_WIDTH); 
      008796 4B 20            [ 1] 1506 	push	#0x20
      008798 4B 31            [ 1] 1507 	push	#0x31
      00879A CD 80 CE         [ 4] 1508 	call	_write_spi_reg
      00879D 5B 02            [ 2] 1509 	addw	sp, #2
                                   1510 ;	se8r01-receive-pwm.c: 514: write_spi_reg(WRITE_REG|iRF_BANK0_CONFIG, 0x3f); 
      00879F 4B 3F            [ 1] 1511 	push	#0x3f
      0087A1 4B 20            [ 1] 1512 	push	#0x20
      0087A3 CD 80 CE         [ 4] 1513 	call	_write_spi_reg
      0087A6 5B 02            [ 2] 1514 	addw	sp, #2
                                   1515 ;	se8r01-receive-pwm.c: 515: write_spi_reg(WRITE_REG|iRF_BANK0_DYNPD, 0b00111111);          // enable dynamic payload length data
      0087A8 4B 3F            [ 1] 1516 	push	#0x3f
      0087AA 4B 3C            [ 1] 1517 	push	#0x3c
      0087AC CD 80 CE         [ 4] 1518 	call	_write_spi_reg
      0087AF 5B 02            [ 2] 1519 	addw	sp, #2
                                   1520 ;	se8r01-receive-pwm.c: 516: write_spi_reg(WRITE_REG|iRF_BANK0_FEATURE, 0x07);        // enable dynamic paload lenght; enbale payload with ack enable w_tx_payload_noack
      0087B1 4B 07            [ 1] 1521 	push	#0x07
      0087B3 4B 3D            [ 1] 1522 	push	#0x3d
      0087B5 CD 80 CE         [ 4] 1523 	call	_write_spi_reg
      0087B8 5B 02            [ 2] 1524 	addw	sp, #2
                                   1525 ;	se8r01-receive-pwm.c: 517: PC_ODR |= (1 << CE);
      0087BA AE 50 0A         [ 2] 1526 	ldw	x, #0x500a
      0087BD F6               [ 1] 1527 	ld	a, (x)
      0087BE AA 10            [ 1] 1528 	or	a, #0x10
      0087C0 F7               [ 1] 1529 	ld	(x), a
      0087C1 5B 05            [ 2] 1530 	addw	sp, #5
      0087C3 81               [ 4] 1531 	ret
                                   1532 ;	se8r01-receive-pwm.c: 522: void Init_Tim2 ()
                                   1533 ;	-----------------------------------------
                                   1534 ;	 function Init_Tim2
                                   1535 ;	-----------------------------------------
      0087C4                       1536 _Init_Tim2:
                                   1537 ;	se8r01-receive-pwm.c: 551: TIM2_CCMR3 |=0X70;//Set the timer 2 / three channel three (PD2) output mode
      0087C4 AE 53 09         [ 2] 1538 	ldw	x, #0x5309
      0087C7 F6               [ 1] 1539 	ld	a, (x)
      0087C8 AA 70            [ 1] 1540 	or	a, #0x70
      0087CA F7               [ 1] 1541 	ld	(x), a
                                   1542 ;	se8r01-receive-pwm.c: 552: TIM2_CCMR3 |=0X04;//Comparison of 3 pre load / / output enable
      0087CB AE 53 09         [ 2] 1543 	ldw	x, #0x5309
      0087CE F6               [ 1] 1544 	ld	a, (x)
      0087CF AA 04            [ 1] 1545 	or	a, #0x04
      0087D1 F7               [ 1] 1546 	ld	(x), a
                                   1547 ;	se8r01-receive-pwm.c: 554: TIM2_CCER2 |=0x03;//  Channel 3 enable, active low output configuration
      0087D2 AE 53 0B         [ 2] 1548 	ldw	x, #0x530b
      0087D5 F6               [ 1] 1549 	ld	a, (x)
      0087D6 AA 03            [ 1] 1550 	or	a, #0x03
      0087D8 F7               [ 1] 1551 	ld	(x), a
                                   1552 ;	se8r01-receive-pwm.c: 557: TIM2_PSCR =0X04;// Automatic loading / / initialization register, PWM Fang Bo frequency, Fpwm=0.125M/62500=2HZ
      0087D9 AE 53 0E         [ 2] 1553 	ldw	x, #0x530e
      0087DC A6 04            [ 1] 1554 	ld	a, #0x04
      0087DE F7               [ 1] 1555 	ld	(x), a
                                   1556 ;	se8r01-receive-pwm.c: 558: TIM2_ARRH =62500/256; //auto reload register value
      0087DF AE 53 0F         [ 2] 1557 	ldw	x, #0x530f
      0087E2 A6 F4            [ 1] 1558 	ld	a, #0xf4
      0087E4 F7               [ 1] 1559 	ld	(x), a
                                   1560 ;	se8r01-receive-pwm.c: 559: TIM2_ARRL =62500%256;
      0087E5 AE 53 10         [ 2] 1561 	ldw	x, #0x5310
      0087E8 A6 24            [ 1] 1562 	ld	a, #0x24
      0087EA F7               [ 1] 1563 	ld	(x), a
                                   1564 ;	se8r01-receive-pwm.c: 561: TIM2_CCR3H =31250/256; //compare capture register value
      0087EB AE 53 15         [ 2] 1565 	ldw	x, #0x5315
      0087EE A6 7A            [ 1] 1566 	ld	a, #0x7a
      0087F0 F7               [ 1] 1567 	ld	(x), a
                                   1568 ;	se8r01-receive-pwm.c: 562: TIM2_CCR3L =31250%256;
      0087F1 AE 53 16         [ 2] 1569 	ldw	x, #0x5316
      0087F4 A6 12            [ 1] 1570 	ld	a, #0x12
      0087F6 F7               [ 1] 1571 	ld	(x), a
                                   1572 ;	se8r01-receive-pwm.c: 566: TIM2_CR1 |=0x81;
      0087F7 AE 53 00         [ 2] 1573 	ldw	x, #0x5300
      0087FA F6               [ 1] 1574 	ld	a, (x)
      0087FB AA 81            [ 1] 1575 	or	a, #0x81
      0087FD F7               [ 1] 1576 	ld	(x), a
      0087FE 81               [ 4] 1577 	ret
                                   1578 ;	se8r01-receive-pwm.c: 573: int main () {
                                   1579 ;	-----------------------------------------
                                   1580 ;	 function main
                                   1581 ;	-----------------------------------------
      0087FF                       1582 _main:
      0087FF 52 33            [ 2] 1583 	sub	sp, #51
                                   1584 ;	se8r01-receive-pwm.c: 575: UCHAR rx_addr_p1[]  = { 0xd2, 0xf0, 0xf0, 0xf0, 0xf0 };
      008801 90 96            [ 1] 1585 	ldw	y, sp
      008803 72 A9 00 2D      [ 2] 1586 	addw	y, #45
      008807 A6 D2            [ 1] 1587 	ld	a, #0xd2
      008809 90 F7            [ 1] 1588 	ld	(y), a
      00880B 93               [ 1] 1589 	ldw	x, y
      00880C 5C               [ 2] 1590 	incw	x
      00880D A6 F0            [ 1] 1591 	ld	a, #0xf0
      00880F F7               [ 1] 1592 	ld	(x), a
      008810 93               [ 1] 1593 	ldw	x, y
      008811 5C               [ 2] 1594 	incw	x
      008812 5C               [ 2] 1595 	incw	x
      008813 A6 F0            [ 1] 1596 	ld	a, #0xf0
      008815 F7               [ 1] 1597 	ld	(x), a
      008816 93               [ 1] 1598 	ldw	x, y
      008817 A6 F0            [ 1] 1599 	ld	a, #0xf0
      008819 E7 03            [ 1] 1600 	ld	(0x0003, x), a
      00881B 93               [ 1] 1601 	ldw	x, y
      00881C A6 F0            [ 1] 1602 	ld	a, #0xf0
      00881E E7 04            [ 1] 1603 	ld	(0x0004, x), a
                                   1604 ;	se8r01-receive-pwm.c: 576: UCHAR tx_addr[]     = { 0xe1, 0xf0, 0xf0, 0xf0, 0xf0 };
      008820 90 96            [ 1] 1605 	ldw	y, sp
      008822 72 A9 00 22      [ 2] 1606 	addw	y, #34
      008826 A6 E1            [ 1] 1607 	ld	a, #0xe1
      008828 90 F7            [ 1] 1608 	ld	(y), a
      00882A 93               [ 1] 1609 	ldw	x, y
      00882B 5C               [ 2] 1610 	incw	x
      00882C A6 F0            [ 1] 1611 	ld	a, #0xf0
      00882E F7               [ 1] 1612 	ld	(x), a
      00882F 93               [ 1] 1613 	ldw	x, y
      008830 5C               [ 2] 1614 	incw	x
      008831 5C               [ 2] 1615 	incw	x
      008832 A6 F0            [ 1] 1616 	ld	a, #0xf0
      008834 F7               [ 1] 1617 	ld	(x), a
      008835 93               [ 1] 1618 	ldw	x, y
      008836 A6 F0            [ 1] 1619 	ld	a, #0xf0
      008838 E7 03            [ 1] 1620 	ld	(0x0003, x), a
      00883A 93               [ 1] 1621 	ldw	x, y
      00883B 1C 00 04         [ 2] 1622 	addw	x, #0x0004
      00883E A6 F0            [ 1] 1623 	ld	a, #0xf0
      008840 F7               [ 1] 1624 	ld	(x), a
                                   1625 ;	se8r01-receive-pwm.c: 581: InitializeSystemClock();
      008841 CD 81 E4         [ 4] 1626 	call	_InitializeSystemClock
                                   1627 ;	se8r01-receive-pwm.c: 582: InitializeUART();
      008844 CD 82 DC         [ 4] 1628 	call	_InitializeUART
                                   1629 ;	se8r01-receive-pwm.c: 584: InitializeSPI ();
      008847 CD 81 BC         [ 4] 1630 	call	_InitializeSPI
                                   1631 ;	se8r01-receive-pwm.c: 586: UARTPrintF("start debug \n\r");
      00884A AE 89 8B         [ 2] 1632 	ldw	x, #___str_0+0
      00884D 89               [ 2] 1633 	pushw	x
      00884E CD 82 79         [ 4] 1634 	call	_UARTPrintF
      008851 5B 02            [ 2] 1635 	addw	sp, #2
                                   1636 ;	se8r01-receive-pwm.c: 588: memset (tx_payload, 0, sizeof(tx_payload));
      008853 96               [ 1] 1637 	ldw	x, sp
      008854 5C               [ 2] 1638 	incw	x
      008855 4B 21            [ 1] 1639 	push	#0x21
      008857 4B 00            [ 1] 1640 	push	#0x00
      008859 4B 00            [ 1] 1641 	push	#0x00
      00885B 4B 00            [ 1] 1642 	push	#0x00
      00885D 89               [ 2] 1643 	pushw	x
      00885E CD 8A 22         [ 4] 1644 	call	_memset
      008861 5B 06            [ 2] 1645 	addw	sp, #6
                                   1646 ;	se8r01-receive-pwm.c: 591: init_io();                        // Initialize IO port
      008863 CD 83 55         [ 4] 1647 	call	_init_io
                                   1648 ;	se8r01-receive-pwm.c: 592: write_spi_reg(FLUSH_RX,0); // receive data 
      008866 4B 00            [ 1] 1649 	push	#0x00
      008868 4B E2            [ 1] 1650 	push	#0xe2
      00886A CD 80 CE         [ 4] 1651 	call	_write_spi_reg
      00886D 5B 02            [ 2] 1652 	addw	sp, #2
                                   1653 ;	se8r01-receive-pwm.c: 593: readstatus = read_spi_reg(CONFIG);
      00886F 4B 00            [ 1] 1654 	push	#0x00
      008871 CD 81 0A         [ 4] 1655 	call	_read_spi_reg
      008874 5B 01            [ 2] 1656 	addw	sp, #1
                                   1657 ;	se8r01-receive-pwm.c: 594: UARTPrintF("config = \n\r");
      008876 AE 89 9A         [ 2] 1658 	ldw	x, #___str_1+0
      008879 88               [ 1] 1659 	push	a
      00887A 89               [ 2] 1660 	pushw	x
      00887B CD 82 79         [ 4] 1661 	call	_UARTPrintF
      00887E 5B 02            [ 2] 1662 	addw	sp, #2
      008880 84               [ 1] 1663 	pop	a
                                   1664 ;	se8r01-receive-pwm.c: 595: print_UCHAR_hex(readstatus);
      008881 88               [ 1] 1665 	push	a
      008882 CD 82 90         [ 4] 1666 	call	_print_UCHAR_hex
      008885 84               [ 1] 1667 	pop	a
                                   1668 ;	se8r01-receive-pwm.c: 596: readstatus = read_spi_reg(STATUS);
      008886 4B 07            [ 1] 1669 	push	#0x07
      008888 CD 81 0A         [ 4] 1670 	call	_read_spi_reg
      00888B 5B 01            [ 2] 1671 	addw	sp, #1
                                   1672 ;	se8r01-receive-pwm.c: 597: UARTPrintF("status = \n\r");
      00888D AE 89 A6         [ 2] 1673 	ldw	x, #___str_2+0
      008890 88               [ 1] 1674 	push	a
      008891 89               [ 2] 1675 	pushw	x
      008892 CD 82 79         [ 4] 1676 	call	_UARTPrintF
      008895 5B 02            [ 2] 1677 	addw	sp, #2
      008897 84               [ 1] 1678 	pop	a
                                   1679 ;	se8r01-receive-pwm.c: 598: print_UCHAR_hex(readstatus);
      008898 88               [ 1] 1680 	push	a
      008899 CD 82 90         [ 4] 1681 	call	_print_UCHAR_hex
      00889C 84               [ 1] 1682 	pop	a
                                   1683 ;	se8r01-receive-pwm.c: 600: Init_Tim2 (); //pwm for led on pd2
      00889D CD 87 C4         [ 4] 1684 	call	_Init_Tim2
                                   1685 ;	se8r01-receive-pwm.c: 601: PD_DDR |= (1<<2);
      0088A0 AE 50 11         [ 2] 1686 	ldw	x, #0x5011
      0088A3 F6               [ 1] 1687 	ld	a, (x)
      0088A4 AA 04            [ 1] 1688 	or	a, #0x04
      0088A6 F7               [ 1] 1689 	ld	(x), a
                                   1690 ;	se8r01-receive-pwm.c: 602: PD_CR1 |= (1<<2);
      0088A7 AE 50 12         [ 2] 1691 	ldw	x, #0x5012
      0088AA F6               [ 1] 1692 	ld	a, (x)
      0088AB AA 04            [ 1] 1693 	or	a, #0x04
      0088AD F7               [ 1] 1694 	ld	(x), a
                                   1695 ;	se8r01-receive-pwm.c: 603: PD_CR2 &= 0xFD;
      0088AE AE 50 13         [ 2] 1696 	ldw	x, #0x5013
      0088B1 F6               [ 1] 1697 	ld	a, (x)
      0088B2 A4 FD            [ 1] 1698 	and	a, #0xfd
      0088B4 F7               [ 1] 1699 	ld	(x), a
                                   1700 ;	se8r01-receive-pwm.c: 604: SE8R01_Init();
      0088B5 CD 86 DE         [ 4] 1701 	call	_SE8R01_Init
                                   1702 ;	se8r01-receive-pwm.c: 605: UARTPrintF("timer initialised = \n\r");
      0088B8 AE 89 B2         [ 2] 1703 	ldw	x, #___str_3+0
      0088BB 89               [ 2] 1704 	pushw	x
      0088BC CD 82 79         [ 4] 1705 	call	_UARTPrintF
      0088BF 5B 02            [ 2] 1706 	addw	sp, #2
                                   1707 ;	se8r01-receive-pwm.c: 608: while (1) {
      0088C1                       1708 00110$:
                                   1709 ;	se8r01-receive-pwm.c: 610: if ((PD_IDR & (1 << 3))==0) //input low
      0088C1 AE 50 10         [ 2] 1710 	ldw	x, #0x5010
      0088C4 F6               [ 1] 1711 	ld	a, (x)
      0088C5 A5 08            [ 1] 1712 	bcp	a, #0x08
      0088C7 27 03            [ 1] 1713 	jreq	00170$
      0088C9 CC 89 51         [ 2] 1714 	jp	00105$
      0088CC                       1715 00170$:
                                   1716 ;	se8r01-receive-pwm.c: 614: delay(240);
      0088CC 4B F0            [ 1] 1717 	push	#0xf0
      0088CE 4B 00            [ 1] 1718 	push	#0x00
      0088D0 CD 82 2E         [ 4] 1719 	call	_delay
      0088D3 5B 02            [ 2] 1720 	addw	sp, #2
                                   1721 ;	se8r01-receive-pwm.c: 615: signal_lv=read_spi_reg(iRF_BANK0_RPD);
      0088D5 4B 09            [ 1] 1722 	push	#0x09
      0088D7 CD 81 0A         [ 4] 1723 	call	_read_spi_reg
      0088DA 5B 01            [ 2] 1724 	addw	sp, #1
      0088DC C7 00 1A         [ 1] 1725 	ld	_signal_lv+0, a
                                   1726 ;	se8r01-receive-pwm.c: 616: status = read_spi_reg(STATUS);
      0088DF 4B 07            [ 1] 1727 	push	#0x07
      0088E1 CD 81 0A         [ 4] 1728 	call	_read_spi_reg
      0088E4 5B 01            [ 2] 1729 	addw	sp, #1
      0088E6 C7 00 1D         [ 1] 1730 	ld	_status+0, a
                                   1731 ;	se8r01-receive-pwm.c: 618: if(status&STA_MARK_RX)                                                 // if receive data ready (TX_DS) interrupt
      0088E9 72 06 00 1D 02   [ 2] 1732 	btjt	_status+0, #6, 00171$
      0088EE 20 57            [ 2] 1733 	jra	00103$
      0088F0                       1734 00171$:
                                   1735 ;	se8r01-receive-pwm.c: 621: pip= (status & 0b00001110)>>1;
      0088F0 C6 00 1D         [ 1] 1736 	ld	a, _status+0
      0088F3 A4 0E            [ 1] 1737 	and	a, #0x0e
      0088F5 44               [ 1] 1738 	srl	a
      0088F6 5F               [ 1] 1739 	clrw	x
      0088F7 97               [ 1] 1740 	ld	xl, a
      0088F8 CF 00 1B         [ 2] 1741 	ldw	_pip+0, x
                                   1742 ;	se8r01-receive-pwm.c: 622: pload_width_now=read_spi_reg(iRF_CMD_R_RX_PL_WID);
      0088FB 4B 60            [ 1] 1743 	push	#0x60
      0088FD CD 81 0A         [ 4] 1744 	call	_read_spi_reg
      008900 5B 01            [ 2] 1745 	addw	sp, #1
      008902 5F               [ 1] 1746 	clrw	x
      008903 97               [ 1] 1747 	ld	xl, a
      008904 CF 00 16         [ 2] 1748 	ldw	_pload_width_now+0, x
                                   1749 ;	se8r01-receive-pwm.c: 623: read_spi_buf(RD_RX_PLOAD, rx_buf,32);             // read playload to rx_buf
      008907 AE 00 2E         [ 2] 1750 	ldw	x, #_rx_buf+0
      00890A 1F 32            [ 2] 1751 	ldw	(0x32, sp), x
      00890C 1E 32            [ 2] 1752 	ldw	x, (0x32, sp)
      00890E 4B 20            [ 1] 1753 	push	#0x20
      008910 89               [ 2] 1754 	pushw	x
      008911 4B 61            [ 1] 1755 	push	#0x61
      008913 CD 81 80         [ 4] 1756 	call	_read_spi_buf
      008916 5B 04            [ 2] 1757 	addw	sp, #4
                                   1758 ;	se8r01-receive-pwm.c: 624: write_spi_reg(FLUSH_RX,0);
      008918 4B 00            [ 1] 1759 	push	#0x00
      00891A 4B E2            [ 1] 1760 	push	#0xe2
      00891C CD 80 CE         [ 4] 1761 	call	_write_spi_reg
      00891F 5B 02            [ 2] 1762 	addw	sp, #2
                                   1763 ;	se8r01-receive-pwm.c: 626: newdata=1;
      008921 35 01 00 19      [ 1] 1764 	mov	_newdata+1, #0x01
      008925 72 5F 00 18      [ 1] 1765 	clr	_newdata+0
                                   1766 ;	se8r01-receive-pwm.c: 627: for (teller=0;teller<32;++teller)
      008929 5F               [ 1] 1767 	clrw	x
      00892A                       1768 00112$:
                                   1769 ;	se8r01-receive-pwm.c: 628: print_UCHAR_hex (rx_buf[teller]);
      00892A 90 93            [ 1] 1770 	ldw	y, x
      00892C 72 F9 32         [ 2] 1771 	addw	y, (0x32, sp)
      00892F 90 F6            [ 1] 1772 	ld	a, (y)
      008931 89               [ 2] 1773 	pushw	x
      008932 88               [ 1] 1774 	push	a
      008933 CD 82 90         [ 4] 1775 	call	_print_UCHAR_hex
      008936 84               [ 1] 1776 	pop	a
      008937 85               [ 2] 1777 	popw	x
                                   1778 ;	se8r01-receive-pwm.c: 627: for (teller=0;teller<32;++teller)
      008938 5C               [ 2] 1779 	incw	x
      008939 A3 00 20         [ 2] 1780 	cpw	x, #0x0020
      00893C 2F EC            [ 1] 1781 	jrslt	00112$
                                   1782 ;	se8r01-receive-pwm.c: 629: UARTPrintF("\n\r");
      00893E AE 89 C9         [ 2] 1783 	ldw	x, #___str_4+0
      008941 89               [ 2] 1784 	pushw	x
      008942 CD 82 79         [ 4] 1785 	call	_UARTPrintF
      008945 5B 02            [ 2] 1786 	addw	sp, #2
      008947                       1787 00103$:
                                   1788 ;	se8r01-receive-pwm.c: 632: write_spi_reg(WRITE_REG+STATUS,status);       // clear RX_DR or TX_DS or MAX_RT interrupt flag
      008947 3B 00 1D         [ 1] 1789 	push	_status+0
      00894A 4B 27            [ 1] 1790 	push	#0x27
      00894C CD 80 CE         [ 4] 1791 	call	_write_spi_reg
      00894F 5B 02            [ 2] 1792 	addw	sp, #2
      008951                       1793 00105$:
                                   1794 ;	se8r01-receive-pwm.c: 637: for (x1 = 0; x1 < 50; ++x1)
      008951 5F               [ 1] 1795 	clrw	x
      008952 1F 2B            [ 2] 1796 	ldw	(0x2b, sp), x
      008954                       1797 00121$:
      008954 1E 2B            [ 2] 1798 	ldw	x, (0x2b, sp)
      008956 A3 00 32         [ 2] 1799 	cpw	x, #0x0032
      008959 2F 03            [ 1] 1800 	jrslt	00173$
      00895B CC 88 C1         [ 2] 1801 	jp	00110$
      00895E                       1802 00173$:
                                   1803 ;	se8r01-receive-pwm.c: 638: for (y1 = 0; y1 < 50; ++y1)
      00895E 5F               [ 1] 1804 	clrw	x
      00895F 1F 29            [ 2] 1805 	ldw	(0x29, sp), x
      008961                       1806 00118$:
      008961 1E 29            [ 2] 1807 	ldw	x, (0x29, sp)
      008963 A3 00 32         [ 2] 1808 	cpw	x, #0x0032
      008966 2E 19            [ 1] 1809 	jrsge	00122$
                                   1810 ;	se8r01-receive-pwm.c: 639: for (z1 = 0; z1 < 50; ++z1)
      008968 5F               [ 1] 1811 	clrw	x
      008969 1F 27            [ 2] 1812 	ldw	(0x27, sp), x
      00896B                       1813 00115$:
      00896B 1E 27            [ 2] 1814 	ldw	x, (0x27, sp)
      00896D A3 00 32         [ 2] 1815 	cpw	x, #0x0032
      008970 2E 08            [ 1] 1816 	jrsge	00119$
                                   1817 ;	se8r01-receive-pwm.c: 640: __asm__("nop");
      008972 9D               [ 1] 1818 	nop
                                   1819 ;	se8r01-receive-pwm.c: 639: for (z1 = 0; z1 < 50; ++z1)
      008973 1E 27            [ 2] 1820 	ldw	x, (0x27, sp)
      008975 5C               [ 2] 1821 	incw	x
      008976 1F 27            [ 2] 1822 	ldw	(0x27, sp), x
      008978 20 F1            [ 2] 1823 	jra	00115$
      00897A                       1824 00119$:
                                   1825 ;	se8r01-receive-pwm.c: 638: for (y1 = 0; y1 < 50; ++y1)
      00897A 1E 29            [ 2] 1826 	ldw	x, (0x29, sp)
      00897C 5C               [ 2] 1827 	incw	x
      00897D 1F 29            [ 2] 1828 	ldw	(0x29, sp), x
      00897F 20 E0            [ 2] 1829 	jra	00118$
      008981                       1830 00122$:
                                   1831 ;	se8r01-receive-pwm.c: 637: for (x1 = 0; x1 < 50; ++x1)
      008981 1E 2B            [ 2] 1832 	ldw	x, (0x2b, sp)
      008983 5C               [ 2] 1833 	incw	x
      008984 1F 2B            [ 2] 1834 	ldw	(0x2b, sp), x
      008986 20 CC            [ 2] 1835 	jra	00121$
      008988 5B 33            [ 2] 1836 	addw	sp, #51
      00898A 81               [ 4] 1837 	ret
                                   1838 	.area CODE
      00898B                       1839 ___str_0:
      00898B 73 74 61 72 74 20 64  1840 	.ascii "start debug "
             65 62 75 67 20
      008997 0A                    1841 	.db 0x0A
      008998 0D                    1842 	.db 0x0D
      008999 00                    1843 	.db 0x00
      00899A                       1844 ___str_1:
      00899A 63 6F 6E 66 69 67 20  1845 	.ascii "config = "
             3D 20
      0089A3 0A                    1846 	.db 0x0A
      0089A4 0D                    1847 	.db 0x0D
      0089A5 00                    1848 	.db 0x00
      0089A6                       1849 ___str_2:
      0089A6 73 74 61 74 75 73 20  1850 	.ascii "status = "
             3D 20
      0089AF 0A                    1851 	.db 0x0A
      0089B0 0D                    1852 	.db 0x0D
      0089B1 00                    1853 	.db 0x00
      0089B2                       1854 ___str_3:
      0089B2 74 69 6D 65 72 20 69  1855 	.ascii "timer initialised = "
             6E 69 74 69 61 6C 69
             73 65 64 20 3D 20
      0089C6 0A                    1856 	.db 0x0A
      0089C7 0D                    1857 	.db 0x0D
      0089C8 00                    1858 	.db 0x00
      0089C9                       1859 ___str_4:
      0089C9 0A                    1860 	.db 0x0A
      0089CA 0D                    1861 	.db 0x0D
      0089CB 00                    1862 	.db 0x00
                                   1863 	.area INITIALIZER
      008A41                       1864 __xinit__SE8R01_DR_2M:
      008A41 00 00                 1865 	.dw #0x0000
      008A43                       1866 __xinit__SE8R01_DR_1M:
      008A43 00 00                 1867 	.dw #0x0000
      008A45                       1868 __xinit__SE8R01_DR_500K:
      008A45 00 01                 1869 	.dw #0x0001
      008A47                       1870 __xinit__pload_width_now:
      008A47 00 00                 1871 	.dw #0x0000
      008A49                       1872 __xinit__newdata:
      008A49 00 00                 1873 	.dw #0x0000
      008A4B                       1874 __xinit__signal_lv:
      008A4B 00                    1875 	.db #0x00	;  0
      008A4C                       1876 __xinit__pip:
      008A4C 00 00                 1877 	.dw #0x0000
      008A4E                       1878 __xinit__status:
      008A4E 00                    1879 	.db #0x00	; 0
      008A4F                       1880 __xinit__TX_ADDRESS:
      008A4F B3                    1881 	.db #0xB3	; 179
      008A50 43                    1882 	.db #0x43	; 67	'C'
      008A51 10                    1883 	.db #0x10	; 16
      008A52 10                    1884 	.db #0x10	; 16
      008A53                       1885 __xinit__ADDRESS2:
      008A53 B1                    1886 	.db #0xB1	; 177
      008A54                       1887 __xinit__ADDRESS3:
      008A54 B2                    1888 	.db #0xB2	; 178
      008A55                       1889 __xinit__ADDRESS4:
      008A55 B3                    1890 	.db #0xB3	; 179
      008A56                       1891 __xinit__ADDRESS5:
      008A56 B4                    1892 	.db #0xB4	; 180
      008A57                       1893 __xinit__ADDRESS1:
      008A57 B0                    1894 	.db #0xB0	; 176
      008A58 43                    1895 	.db #0x43	; 67	'C'
      008A59 10                    1896 	.db #0x10	; 16
      008A5A 10                    1897 	.db #0x10	; 16
      008A5B                       1898 __xinit__ADDRESS0:
      008A5B 34                    1899 	.db #0x34	; 52	'4'
      008A5C 43                    1900 	.db #0x43	; 67	'C'
      008A5D 10                    1901 	.db #0x10	; 16
      008A5E 10                    1902 	.db #0x10	; 16
      008A5F                       1903 __xinit__rx_buf:
      008A5F 00                    1904 	.db #0x00	; 0
      008A60 00                    1905 	.db 0x00
      008A61 00                    1906 	.db 0x00
      008A62 00                    1907 	.db 0x00
      008A63 00                    1908 	.db 0x00
      008A64 00                    1909 	.db 0x00
      008A65 00                    1910 	.db 0x00
      008A66 00                    1911 	.db 0x00
      008A67 00                    1912 	.db 0x00
      008A68 00                    1913 	.db 0x00
      008A69 00                    1914 	.db 0x00
      008A6A 00                    1915 	.db 0x00
      008A6B 00                    1916 	.db 0x00
      008A6C 00                    1917 	.db 0x00
      008A6D 00                    1918 	.db 0x00
      008A6E 00                    1919 	.db 0x00
      008A6F 00                    1920 	.db 0x00
      008A70 00                    1921 	.db 0x00
      008A71 00                    1922 	.db 0x00
      008A72 00                    1923 	.db 0x00
      008A73 00                    1924 	.db 0x00
      008A74 00                    1925 	.db 0x00
      008A75 00                    1926 	.db 0x00
      008A76 00                    1927 	.db 0x00
      008A77 00                    1928 	.db 0x00
      008A78 00                    1929 	.db 0x00
      008A79 00                    1930 	.db 0x00
      008A7A 00                    1931 	.db 0x00
      008A7B 00                    1932 	.db 0x00
      008A7C 00                    1933 	.db 0x00
      008A7D 00                    1934 	.db 0x00
      008A7E 00                    1935 	.db 0x00
      008A7F                       1936 __xinit__tx_buf:
      008A7F 00                    1937 	.db #0x00	; 0
      008A80 00                    1938 	.db 0x00
      008A81 00                    1939 	.db 0x00
      008A82 00                    1940 	.db 0x00
      008A83 00                    1941 	.db 0x00
      008A84 00                    1942 	.db 0x00
      008A85 00                    1943 	.db 0x00
      008A86 00                    1944 	.db 0x00
      008A87 00                    1945 	.db 0x00
      008A88 00                    1946 	.db 0x00
      008A89 00                    1947 	.db 0x00
      008A8A 00                    1948 	.db 0x00
      008A8B 00                    1949 	.db 0x00
      008A8C 00                    1950 	.db 0x00
      008A8D 00                    1951 	.db 0x00
      008A8E 00                    1952 	.db 0x00
      008A8F 00                    1953 	.db 0x00
      008A90 00                    1954 	.db 0x00
      008A91 00                    1955 	.db 0x00
      008A92 00                    1956 	.db 0x00
      008A93 00                    1957 	.db 0x00
      008A94 00                    1958 	.db 0x00
      008A95 00                    1959 	.db 0x00
      008A96 00                    1960 	.db 0x00
      008A97 00                    1961 	.db 0x00
      008A98 00                    1962 	.db 0x00
      008A99 00                    1963 	.db 0x00
      008A9A 00                    1964 	.db 0x00
      008A9B 00                    1965 	.db 0x00
      008A9C 00                    1966 	.db 0x00
      008A9D 00                    1967 	.db 0x00
      008A9E 00                    1968 	.db 0x00
                                   1969 	.area CABS (ABS)

                                      1 ;--------------------------------------------------------
                                      2 ; File Created by SDCC : free open source ANSI-C Compiler
                                      3 ; Version 3.4.0 #8981 (Apr  5 2014) (MINGW32)
                                      4 ; This file was generated Thu Apr 09 13:21:40 2015
                                      5 ;--------------------------------------------------------
                                      6 	.module stm8s_gpio
                                      7 	.optsdcc -mstm8
                                      8 	
                                      9 ;--------------------------------------------------------
                                     10 ; Public variables in this module
                                     11 ;--------------------------------------------------------
                                     12 	.globl _GPIO_DeInit
                                     13 	.globl _GPIO_Init
                                     14 	.globl _GPIO_Write
                                     15 	.globl _GPIO_WriteHigh
                                     16 	.globl _GPIO_WriteLow
                                     17 	.globl _GPIO_WriteReverse
                                     18 	.globl _GPIO_ReadOutputData
                                     19 	.globl _GPIO_ReadInputData
                                     20 	.globl _GPIO_ReadInputPin
                                     21 	.globl _GPIO_ExternalPullUpConfig
                                     22 ;--------------------------------------------------------
                                     23 ; ram data
                                     24 ;--------------------------------------------------------
                                     25 	.area DATA
                                     26 ;--------------------------------------------------------
                                     27 ; ram data
                                     28 ;--------------------------------------------------------
                                     29 	.area INITIALIZED
                                     30 ;--------------------------------------------------------
                                     31 ; absolute external ram data
                                     32 ;--------------------------------------------------------
                                     33 	.area DABS (ABS)
                                     34 ;--------------------------------------------------------
                                     35 ; global & static initialisations
                                     36 ;--------------------------------------------------------
                                     37 	.area HOME
                                     38 	.area GSINIT
                                     39 	.area GSFINAL
                                     40 	.area GSINIT
                                     41 ;--------------------------------------------------------
                                     42 ; Home
                                     43 ;--------------------------------------------------------
                                     44 	.area HOME
                                     45 	.area HOME
                                     46 ;--------------------------------------------------------
                                     47 ; code
                                     48 ;--------------------------------------------------------
                                     49 	.area CODE
                                     50 ;	src\stm8s_gpio.c: 53: void GPIO_DeInit(GPIO_TypeDef* GPIOx)
                                     51 ;	-----------------------------------------
                                     52 ;	 function GPIO_DeInit
                                     53 ;	-----------------------------------------
      008647                         54 _GPIO_DeInit:
                                     55 ;	src\stm8s_gpio.c: 55: GPIOx->ODR = GPIO_ODR_RESET_VALUE; /* Reset Output Data Register */
      008647 16 03            [ 2]   56 	ldw	y, (0x03, sp)
      008649 90 7F            [ 1]   57 	clr	(y)
                                     58 ;	src\stm8s_gpio.c: 56: GPIOx->DDR = GPIO_DDR_RESET_VALUE; /* Reset Data Direction Register */
      00864B 93               [ 1]   59 	ldw	x, y
      00864C 5C               [ 2]   60 	incw	x
      00864D 5C               [ 2]   61 	incw	x
      00864E 7F               [ 1]   62 	clr	(x)
                                     63 ;	src\stm8s_gpio.c: 57: GPIOx->CR1 = GPIO_CR1_RESET_VALUE; /* Reset Control Register 1 */
      00864F 93               [ 1]   64 	ldw	x, y
      008650 1C 00 03         [ 2]   65 	addw	x, #0x0003
      008653 7F               [ 1]   66 	clr	(x)
                                     67 ;	src\stm8s_gpio.c: 58: GPIOx->CR2 = GPIO_CR2_RESET_VALUE; /* Reset Control Register 2 */
      008654 93               [ 1]   68 	ldw	x, y
      008655 1C 00 04         [ 2]   69 	addw	x, #0x0004
      008658 7F               [ 1]   70 	clr	(x)
      008659 81               [ 4]   71 	ret
                                     72 ;	src\stm8s_gpio.c: 71: void GPIO_Init(GPIO_TypeDef* GPIOx, GPIO_Pin_TypeDef GPIO_Pin, GPIO_Mode_TypeDef GPIO_Mode)
                                     73 ;	-----------------------------------------
                                     74 ;	 function GPIO_Init
                                     75 ;	-----------------------------------------
      00865A                         76 _GPIO_Init:
      00865A 52 07            [ 2]   77 	sub	sp, #7
                                     78 ;	src\stm8s_gpio.c: 81: GPIOx->CR2 &= (uint8_t)(~(GPIO_Pin));
      00865C 16 0A            [ 2]   79 	ldw	y, (0x0a, sp)
      00865E 17 06            [ 2]   80 	ldw	(0x06, sp), y
      008660 1E 06            [ 2]   81 	ldw	x, (0x06, sp)
      008662 1C 00 04         [ 2]   82 	addw	x, #0x0004
      008665 1F 04            [ 2]   83 	ldw	(0x04, sp), x
      008667 1E 04            [ 2]   84 	ldw	x, (0x04, sp)
      008669 F6               [ 1]   85 	ld	a, (x)
      00866A 95               [ 1]   86 	ld	xh, a
      00866B 7B 0C            [ 1]   87 	ld	a, (0x0c, sp)
      00866D 43               [ 1]   88 	cpl	a
      00866E 6B 03            [ 1]   89 	ld	(0x03, sp), a
      008670 9E               [ 1]   90 	ld	a, xh
      008671 14 03            [ 1]   91 	and	a, (0x03, sp)
      008673 1E 04            [ 2]   92 	ldw	x, (0x04, sp)
      008675 F7               [ 1]   93 	ld	(x), a
                                     94 ;	src\stm8s_gpio.c: 98: GPIOx->DDR |= (uint8_t)GPIO_Pin;
      008676 1E 06            [ 2]   95 	ldw	x, (0x06, sp)
      008678 5C               [ 2]   96 	incw	x
      008679 5C               [ 2]   97 	incw	x
      00867A 1F 01            [ 2]   98 	ldw	(0x01, sp), x
                                     99 ;	src\stm8s_gpio.c: 87: if ((((uint8_t)(GPIO_Mode)) & (uint8_t)0x80) != (uint8_t)0x00) /* Output mode */
      00867C 7B 0D            [ 1]  100 	ld	a, (0x0d, sp)
      00867E 48               [ 1]  101 	sll	a
      00867F 24 21            [ 1]  102 	jrnc	00105$
                                    103 ;	src\stm8s_gpio.c: 91: GPIOx->ODR |= (uint8_t)GPIO_Pin;
      008681 1E 06            [ 2]  104 	ldw	x, (0x06, sp)
      008683 F6               [ 1]  105 	ld	a, (x)
                                    106 ;	src\stm8s_gpio.c: 89: if ((((uint8_t)(GPIO_Mode)) & (uint8_t)0x10) != (uint8_t)0x00) /* High level */
      008684 88               [ 1]  107 	push	a
      008685 7B 0E            [ 1]  108 	ld	a, (0x0e, sp)
      008687 A5 10            [ 1]  109 	bcp	a, #0x10
      008689 84               [ 1]  110 	pop	a
      00868A 27 07            [ 1]  111 	jreq	00102$
                                    112 ;	src\stm8s_gpio.c: 91: GPIOx->ODR |= (uint8_t)GPIO_Pin;
      00868C 1A 0C            [ 1]  113 	or	a, (0x0c, sp)
      00868E 1E 06            [ 2]  114 	ldw	x, (0x06, sp)
      008690 F7               [ 1]  115 	ld	(x), a
      008691 20 05            [ 2]  116 	jra	00103$
      008693                        117 00102$:
                                    118 ;	src\stm8s_gpio.c: 95: GPIOx->ODR &= (uint8_t)(~(GPIO_Pin));
      008693 14 03            [ 1]  119 	and	a, (0x03, sp)
      008695 1E 06            [ 2]  120 	ldw	x, (0x06, sp)
      008697 F7               [ 1]  121 	ld	(x), a
      008698                        122 00103$:
                                    123 ;	src\stm8s_gpio.c: 98: GPIOx->DDR |= (uint8_t)GPIO_Pin;
      008698 1E 01            [ 2]  124 	ldw	x, (0x01, sp)
      00869A F6               [ 1]  125 	ld	a, (x)
      00869B 1A 0C            [ 1]  126 	or	a, (0x0c, sp)
      00869D 1E 01            [ 2]  127 	ldw	x, (0x01, sp)
      00869F F7               [ 1]  128 	ld	(x), a
      0086A0 20 08            [ 2]  129 	jra	00106$
      0086A2                        130 00105$:
                                    131 ;	src\stm8s_gpio.c: 103: GPIOx->DDR &= (uint8_t)(~(GPIO_Pin));
      0086A2 1E 01            [ 2]  132 	ldw	x, (0x01, sp)
      0086A4 F6               [ 1]  133 	ld	a, (x)
      0086A5 14 03            [ 1]  134 	and	a, (0x03, sp)
      0086A7 1E 01            [ 2]  135 	ldw	x, (0x01, sp)
      0086A9 F7               [ 1]  136 	ld	(x), a
      0086AA                        137 00106$:
                                    138 ;	src\stm8s_gpio.c: 112: GPIOx->CR1 |= (uint8_t)GPIO_Pin;
      0086AA 1E 06            [ 2]  139 	ldw	x, (0x06, sp)
      0086AC 1C 00 03         [ 2]  140 	addw	x, #0x0003
                                    141 ;	src\stm8s_gpio.c: 110: if ((((uint8_t)(GPIO_Mode)) & (uint8_t)0x40) != (uint8_t)0x00) /* Pull-Up or Push-Pull */
      0086AF 7B 0D            [ 1]  142 	ld	a, (0x0d, sp)
      0086B1 A5 40            [ 1]  143 	bcp	a, #0x40
      0086B3 27 06            [ 1]  144 	jreq	00108$
                                    145 ;	src\stm8s_gpio.c: 112: GPIOx->CR1 |= (uint8_t)GPIO_Pin;
      0086B5 F6               [ 1]  146 	ld	a, (x)
      0086B6 1A 0C            [ 1]  147 	or	a, (0x0c, sp)
      0086B8 F7               [ 1]  148 	ld	(x), a
      0086B9 20 04            [ 2]  149 	jra	00109$
      0086BB                        150 00108$:
                                    151 ;	src\stm8s_gpio.c: 116: GPIOx->CR1 &= (uint8_t)(~(GPIO_Pin));
      0086BB F6               [ 1]  152 	ld	a, (x)
      0086BC 14 03            [ 1]  153 	and	a, (0x03, sp)
      0086BE F7               [ 1]  154 	ld	(x), a
      0086BF                        155 00109$:
                                    156 ;	src\stm8s_gpio.c: 123: if ((((uint8_t)(GPIO_Mode)) & (uint8_t)0x20) != (uint8_t)0x00) /* Interrupt or Slow slope */
      0086BF 7B 0D            [ 1]  157 	ld	a, (0x0d, sp)
      0086C1 A5 20            [ 1]  158 	bcp	a, #0x20
      0086C3 27 0A            [ 1]  159 	jreq	00111$
                                    160 ;	src\stm8s_gpio.c: 125: GPIOx->CR2 |= (uint8_t)GPIO_Pin;
      0086C5 1E 04            [ 2]  161 	ldw	x, (0x04, sp)
      0086C7 F6               [ 1]  162 	ld	a, (x)
      0086C8 1A 0C            [ 1]  163 	or	a, (0x0c, sp)
      0086CA 1E 04            [ 2]  164 	ldw	x, (0x04, sp)
      0086CC F7               [ 1]  165 	ld	(x), a
      0086CD 20 08            [ 2]  166 	jra	00113$
      0086CF                        167 00111$:
                                    168 ;	src\stm8s_gpio.c: 129: GPIOx->CR2 &= (uint8_t)(~(GPIO_Pin));
      0086CF 1E 04            [ 2]  169 	ldw	x, (0x04, sp)
      0086D1 F6               [ 1]  170 	ld	a, (x)
      0086D2 14 03            [ 1]  171 	and	a, (0x03, sp)
      0086D4 1E 04            [ 2]  172 	ldw	x, (0x04, sp)
      0086D6 F7               [ 1]  173 	ld	(x), a
      0086D7                        174 00113$:
      0086D7 5B 07            [ 2]  175 	addw	sp, #7
      0086D9 81               [ 4]  176 	ret
                                    177 ;	src\stm8s_gpio.c: 141: void GPIO_Write(GPIO_TypeDef* GPIOx, uint8_t PortVal)
                                    178 ;	-----------------------------------------
                                    179 ;	 function GPIO_Write
                                    180 ;	-----------------------------------------
      0086DA                        181 _GPIO_Write:
                                    182 ;	src\stm8s_gpio.c: 143: GPIOx->ODR = PortVal;
      0086DA 1E 03            [ 2]  183 	ldw	x, (0x03, sp)
      0086DC 7B 05            [ 1]  184 	ld	a, (0x05, sp)
      0086DE F7               [ 1]  185 	ld	(x), a
      0086DF 81               [ 4]  186 	ret
                                    187 ;	src\stm8s_gpio.c: 154: void GPIO_WriteHigh(GPIO_TypeDef* GPIOx, GPIO_Pin_TypeDef PortPins)
                                    188 ;	-----------------------------------------
                                    189 ;	 function GPIO_WriteHigh
                                    190 ;	-----------------------------------------
      0086E0                        191 _GPIO_WriteHigh:
                                    192 ;	src\stm8s_gpio.c: 156: GPIOx->ODR |= (uint8_t)PortPins;
      0086E0 1E 03            [ 2]  193 	ldw	x, (0x03, sp)
      0086E2 F6               [ 1]  194 	ld	a, (x)
      0086E3 1A 05            [ 1]  195 	or	a, (0x05, sp)
      0086E5 F7               [ 1]  196 	ld	(x), a
      0086E6 81               [ 4]  197 	ret
                                    198 ;	src\stm8s_gpio.c: 167: void GPIO_WriteLow(GPIO_TypeDef* GPIOx, GPIO_Pin_TypeDef PortPins)
                                    199 ;	-----------------------------------------
                                    200 ;	 function GPIO_WriteLow
                                    201 ;	-----------------------------------------
      0086E7                        202 _GPIO_WriteLow:
      0086E7 88               [ 1]  203 	push	a
                                    204 ;	src\stm8s_gpio.c: 169: GPIOx->ODR &= (uint8_t)(~PortPins);
      0086E8 1E 04            [ 2]  205 	ldw	x, (0x04, sp)
      0086EA F6               [ 1]  206 	ld	a, (x)
      0086EB 6B 01            [ 1]  207 	ld	(0x01, sp), a
      0086ED 7B 06            [ 1]  208 	ld	a, (0x06, sp)
      0086EF 43               [ 1]  209 	cpl	a
      0086F0 14 01            [ 1]  210 	and	a, (0x01, sp)
      0086F2 F7               [ 1]  211 	ld	(x), a
      0086F3 84               [ 1]  212 	pop	a
      0086F4 81               [ 4]  213 	ret
                                    214 ;	src\stm8s_gpio.c: 180: void GPIO_WriteReverse(GPIO_TypeDef* GPIOx, GPIO_Pin_TypeDef PortPins)
                                    215 ;	-----------------------------------------
                                    216 ;	 function GPIO_WriteReverse
                                    217 ;	-----------------------------------------
      0086F5                        218 _GPIO_WriteReverse:
                                    219 ;	src\stm8s_gpio.c: 182: GPIOx->ODR ^= (uint8_t)PortPins;
      0086F5 1E 03            [ 2]  220 	ldw	x, (0x03, sp)
      0086F7 F6               [ 1]  221 	ld	a, (x)
      0086F8 18 05            [ 1]  222 	xor	a, (0x05, sp)
      0086FA F7               [ 1]  223 	ld	(x), a
      0086FB 81               [ 4]  224 	ret
                                    225 ;	src\stm8s_gpio.c: 191: uint8_t GPIO_ReadOutputData(GPIO_TypeDef* GPIOx)
                                    226 ;	-----------------------------------------
                                    227 ;	 function GPIO_ReadOutputData
                                    228 ;	-----------------------------------------
      0086FC                        229 _GPIO_ReadOutputData:
                                    230 ;	src\stm8s_gpio.c: 193: return ((uint8_t)GPIOx->ODR);
      0086FC 1E 03            [ 2]  231 	ldw	x, (0x03, sp)
      0086FE F6               [ 1]  232 	ld	a, (x)
      0086FF 81               [ 4]  233 	ret
                                    234 ;	src\stm8s_gpio.c: 202: uint8_t GPIO_ReadInputData(GPIO_TypeDef* GPIOx)
                                    235 ;	-----------------------------------------
                                    236 ;	 function GPIO_ReadInputData
                                    237 ;	-----------------------------------------
      008700                        238 _GPIO_ReadInputData:
                                    239 ;	src\stm8s_gpio.c: 204: return ((uint8_t)GPIOx->IDR);
      008700 1E 03            [ 2]  240 	ldw	x, (0x03, sp)
      008702 E6 01            [ 1]  241 	ld	a, (0x1, x)
      008704 81               [ 4]  242 	ret
                                    243 ;	src\stm8s_gpio.c: 213: BitStatus GPIO_ReadInputPin(GPIO_TypeDef* GPIOx, GPIO_Pin_TypeDef GPIO_Pin)
                                    244 ;	-----------------------------------------
                                    245 ;	 function GPIO_ReadInputPin
                                    246 ;	-----------------------------------------
      008705                        247 _GPIO_ReadInputPin:
                                    248 ;	src\stm8s_gpio.c: 215: return ((BitStatus)(GPIOx->IDR & (uint8_t)GPIO_Pin));
      008705 1E 03            [ 2]  249 	ldw	x, (0x03, sp)
      008707 E6 01            [ 1]  250 	ld	a, (0x1, x)
      008709 14 05            [ 1]  251 	and	a, (0x05, sp)
      00870B 81               [ 4]  252 	ret
                                    253 ;	src\stm8s_gpio.c: 225: void GPIO_ExternalPullUpConfig(GPIO_TypeDef* GPIOx, GPIO_Pin_TypeDef GPIO_Pin, FunctionalState NewState)
                                    254 ;	-----------------------------------------
                                    255 ;	 function GPIO_ExternalPullUpConfig
                                    256 ;	-----------------------------------------
      00870C                        257 _GPIO_ExternalPullUpConfig:
      00870C 88               [ 1]  258 	push	a
                                    259 ;	src\stm8s_gpio.c: 233: GPIOx->CR1 |= (uint8_t)GPIO_Pin;
      00870D 1E 04            [ 2]  260 	ldw	x, (0x04, sp)
      00870F 1C 00 03         [ 2]  261 	addw	x, #0x0003
                                    262 ;	src\stm8s_gpio.c: 231: if (NewState != DISABLE) /* External Pull-Up Set*/
      008712 0D 07            [ 1]  263 	tnz	(0x07, sp)
      008714 27 06            [ 1]  264 	jreq	00102$
                                    265 ;	src\stm8s_gpio.c: 233: GPIOx->CR1 |= (uint8_t)GPIO_Pin;
      008716 F6               [ 1]  266 	ld	a, (x)
      008717 1A 06            [ 1]  267 	or	a, (0x06, sp)
      008719 F7               [ 1]  268 	ld	(x), a
      00871A 20 09            [ 2]  269 	jra	00104$
      00871C                        270 00102$:
                                    271 ;	src\stm8s_gpio.c: 236: GPIOx->CR1 &= (uint8_t)(~(GPIO_Pin));
      00871C F6               [ 1]  272 	ld	a, (x)
      00871D 6B 01            [ 1]  273 	ld	(0x01, sp), a
      00871F 7B 06            [ 1]  274 	ld	a, (0x06, sp)
      008721 43               [ 1]  275 	cpl	a
      008722 14 01            [ 1]  276 	and	a, (0x01, sp)
      008724 F7               [ 1]  277 	ld	(x), a
      008725                        278 00104$:
      008725 84               [ 1]  279 	pop	a
      008726 81               [ 4]  280 	ret
                                    281 	.area CODE
                                    282 	.area INITIALIZER
                                    283 	.area CABS (ABS)

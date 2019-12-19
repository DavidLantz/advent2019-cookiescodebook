; Magic Floating DonutZ
     
    ORG $3145
	
CHECK_HACKER_ABILITY:	
	move.w	#1, d0
	cmp.w	#0, d0
	bne	SET_BAKERY_DESTINATION
	jsr HACKER_BAKES

SET_BAKERY_DESTINATION:	
	lea.l	LIDL, a0
	lea.l 	CAR, a1
	move.l	HACKER, d0
	move.l 	d0, (a1)

MOVE_WITHIN_SPEED_LIMIT:
	add.l	$70, a1
	cmp.l	a1, a0
	bne		MOVE_WITHIN_SPEED_LIMIT

EXPLOIT_BAKERY:
	lea	DONUT_SHELF, a1
	lea HACKER, a0
	add.l	#1, a0
	cmp.l	a0, a1
	bne EXPLOIT_BAKERY
	move.l 	DONUTS, d1

SET_HQ_DESTINATION:
	lea		HQ, a0
	lea 	CAR, a1
	move.l	HACKER, d0
	move.l 	d0, (a1)	

HURRY:
	add.l	#110, a1
	cmp.l	a1, a0
	bne		HURRY

TASTE:
	lea	HACKER, a0
	lea	DONUTS, a1
	move.l (a0), (a1)
	move.l #3,d0
	move.l #3,d7
	cmp.l d0,d7
	bne	TASTES_GOOD
	
IMPLEMENT_MAGIC_RECIPIE:
	move.l	#314159265359, d7
	move.w	#42, d3
	move.l	#7, d6
	movel.l #666, d5
	move.l	$1337, d4

PUFFY_MAGIC:
	mulu.l 	d4, d5
	divu.l	d5, d6
	add.l	d7, d6
	sub.w	#1, d3
	swap	d6
	cmp.w	#0,d3
	bne	PUFFY_MAGIC	

FLOAT:						; DONUT IS NOW FLOATING
	lea $dff180, a0				
	lea $dff006, a1
	move.w (a1), (a0)		; DISPLAY FANCY COLORS, EAT AND DANCE
	jmp FLOAT
	
	
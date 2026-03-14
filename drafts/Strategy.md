Moving Averages: {
	period: 30;
		shift:0;
	method: exponential;
		apply: median price (HL/2);	
},
 {
	period: 60;
		shift:0;
	method: exponential;
		apply: median price (HL/2);	
},
 {
	period: 240;
		shift:0;
	method: exponential;
		apply: median price (HL/2);	
};
MACD: {
	name: x4;
		fastEMA: 48 ;
		slowEMA:104;
		MACD SMA:36;
		applyto: Median Price (HL/2)
},
 {
	name:default;
		fastEMA: 12 ;
		slowEMA:26;
		MACD SMA:9;
		applyto: Median Price (HL/2)
},
 {
	name: 1/4;
		fastEMA: 3 ;
		slowEMA:6;
		MACD SMA:2;
		applyto: Median Price (HL/2)
},


# Algorithm:
1. Time frame 5Min
	1. MACD 4x SMA > MACD 4x fastEMA + slowEMA /2
	2. 
	 // Yazeed Hamdan 1201133 Sec.1 
module state_yaz (clk,rst,go,hiway1,hiway2,farm1,farm2);
	input clk,rst,go;
	output reg [1:0] hiway1	;
	output reg [1:0] hiway2;
	output reg [1:0] farm1;
	output reg [1:0] farm2;
	reg [4:0] counter; 	 
 reg [4:0] state;  
	parameter s0 = 5'b00000,	
s1 = 5'b00001,
s2 = 5'b00010,
s3 = 5'b00011,
s4 = 5'b00100,
s5 = 5'b00101,
s6 = 5'b00110,
s7 = 5'b00111,
s8  =5'b01000,
s9 = 5'b01001,
s10 =5'b01010,
s11= 5'b01011,
s12= 5'b01100,
s13= 5'b01101,
s14 =5'b01110,
s15 =5'b01111,
s16 =5'b10000,
s17= 5'b10001;
	
always @(posedge clk or negedge rst)
	begin 	   

		if(rst==0)
			begin
				state <= s0;
				counter<= 5'b00000;
			end 
		else		    
				
				case (state)
		s0:  
			if (counter <  5'b00001 || ~go)
				begin 
					state <= s0;
					if(go)
					counter <= counter +1;
				end
			else
				begin 
					state <= s1;
					counter<=0;
					end
		
		s1:
			
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s1; 
						 if(go)
					counter <= counter +1;
				end
				
				else
				begin 
					state <= s2;
					counter<=0;
					end
		s2:  
			if (counter <  5'b11110 || ~go)
				begin 
					state <= s2;
					if(go)
					counter <= counter +1;
				end 
			   
				else
				begin 
					state <= s3;
					counter<=0;
					end
		
	  	s3:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s3; 
						  if(go)
					counter <= counter +1;
				end  
				else
				begin 
					state <= s4;
					counter<=0;
					end
		
		s4:  
			if (counter <  5'b01010 || ~go)
				begin 
					state <= s4;  
					if(go)
					counter <= counter +1;
				end  
				else
				begin 
					state <= s5;
					counter<=0;
					end
		
		s5:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s5; 
					if(go)
					counter <= counter +1;
				end   
				else
				begin 
					state <= s6;
					counter<=0;
					end
		
		s6:  
			if (counter <  5'b00001 || ~go)
				begin 
					state <= s6;
					if(go)
					counter <= counter +1;
				end    
				else
				begin 
					state <= s7;
					counter<=0;
					end
		
		s7:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s7;
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s8;
					counter<=0;
					end
		
		s8:  
			if (counter <  5'b01111 || ~go)
				begin 
					state <= s8;   
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s9;
					counter<=0;
					end
				
		s9:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s9; 
					if(go)
				     counter <= counter +1;
				end  
				else
				begin 
					state <= s10;
					counter<=0;
					end
		
		s10:  
			if (counter <  5'b00101 || ~go)
				begin 
					state <= s10;
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s11;
					counter<=0;
					end
		
		s11:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s11;
					if(go)
					counter <= counter +1;
				end 
				else
					begin
					
					state <= s12;
					counter<=0;
					end
		
		s12:  
			if (counter <  5'b01010 || ~go)
				begin 
					state <= s12;
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s13;
					counter<=0;
					end
		
		s13:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s13;
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s14;
					counter<=0;
					end
		
		s14:  
			if (counter <  5'b00001 || ~go)
				begin 
					state <= s14;
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s15;
					counter<=0;
					end
		
		s15:  
			if (counter <  5'b00010 || ~go)
				begin 
					state <= s15;
					if(go)
				    counter <= counter +1;
				end 
				else
				begin 
					state <= s16;
					counter<=0;
					end
		s16:  
			if (counter <  5'b01111 || ~go)
				begin 
					state <= s16;
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s17;
					counter<=0;
					end
				
		s17:  
			if (counter <  5'b00011 || ~go)
				begin 
					state <= s17; 
					if(go)
					counter <= counter +1;
				end 
				else
				begin 
					state <= s0;
					counter<=0;
				end	
				default: state <= s0 ;
			endcase 
			end  
// 00 : Green 
//01 : Yellow (when changing from green)
//10 : Red
//11 : Red-Yellow (when changing from red)
		always@(*)
			begin
				case(state)
  		s0:
			begin 		
            	hiway1<= 2'b10;	    
				hiway2<= 2'b10;
    			farm1<=  2'b10;
   			    farm2<= 2'b10; 
			end 
  		s1:
			begin 		
            	hiway1<=2'b11;
				hiway2<= 2'b11 ;
    			farm1<= 2'b10 ;
   			    farm2<= 2'b10 ; 
			end 
   		s2:
			begin 		
            	hiway1<= 2'b00;
				hiway2<= 2'b00;
    			farm1<= 2'b10 ;
   			    farm2<= 2'b10 ; 
			end    
   		s3:
			begin 		
            	hiway1<= 2'b00;
				hiway2<= 2'b01;
    			farm1<= 2'b10;
   			    farm2<= 2'b10; 
			end 
		s4:
			begin 		
            	hiway1<= 2'b00	;
				hiway2<= 2'b10 ;
    			farm1<= 2'b10 ;
   			    farm2<= 2'b10 ; 
			end 	
		s5:
			begin 		
            	hiway1<=  2'b01	;
				hiway2<=  2'b10 ;
    			farm1<= 2'b10 ;
   			    farm2<= 2'b10 ; 
			end     
		s6:
			begin 		
            	hiway1<=  2'b10	;
				hiway2<=  2'b10 ;
    			farm1<= 2'b10 ;
   			    farm2<= 2'b10 ; 
			end 	 
		s7:
			begin 		
            	hiway1<=  2'b10	;
				hiway2<= 2'b10 ;
    			farm1<=  2'b11 ;
   			    farm2<= 2'b11 ; 
			end 
		s8:
		    begin 		
            	hiway1<= 2'b10	;
				hiway2<= 2'b10 ;
    			farm1<= 2'b00 ;
   			    farm2<= 2'b00; 
			end 	
		s9:
			begin 		
            	hiway1<=2'b10;
				hiway2<=2'b10 ;
    			farm1<= 2'b00 ;
   			    farm2<= 2'b01; 
			end 
		s10:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b10;
    			farm1<= 2'b00 ;
   			    farm2<= 2'b01 ; 
			end 
		s11:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b10;
    			farm1<= 2'b01;
   			    farm2<= 2'b11; 
			end 
		s12:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b10;
    			farm1<= 2'b10;
   			    farm2<= 2'b00; 
			end 
		s13:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b10;
    			farm1<= 2'b10;
   			    farm2<= 2'b01; 
			end 
		s14:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b10;
    			farm1<= 2'b10;
   			    farm2<= 2'b10; 
			end 
		s15:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b11;
    			farm1<=  2'b10;
   			    farm2<= 2'b10; 
			end 
		s16:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b00;
    			farm1<= 2'b10;
   			    farm2<= 2'b10; 
			end 
		s17:
			begin 		
            	hiway1<= 2'b10;
				hiway2<= 2'b01;
    			farm1<= 2'b10;
   			    farm2<= 2'b10; 
			end    
			endcase
			end 
		endmodule
// module state_yaz (clk,rst,go,hiway1,hiway2,farm1,farm2);
//	output reg [1:0] hiway2;
//	output reg [1:0] farm1;
//	output reg [1:0] farm2; 

module traffic_tb;
			reg	CLK;		
			reg	RST;
			reg	GO;	
			wire [1:0]Hiway1;
			wire [1:0]Hiway2;
			wire [1:0]Farm1;
			wire [1:0]Farm2;
	state_yaz  stage(CLK,RST,GO,Hiway1,Hiway2,Farm1,Farm2);
	initial
		begin	
	$monitor("when t = %0d  : Highway1 = %b Highway2 = %b farm1 =%b farm2 =%b",$time,Hiway1,Hiway2,Farm1,Farm2);		
		CLK = 0 ;
		RST = 0 ;
		GO = 0 ;
		#10ns RST = ~RST;
		#60ns GO = 1;
		#600ns $finish ;
		end   
		always #5ns CLK = ~CLK;

	endmodule 		
// 00 : Green 
//01 : Yellow (when changing from green)
//10 : Red
//11 : Red-Yellow (when changing from red)
module generateTests(Address,Data);
input [4:0] Address;
output [7:0] Data;
reg [7:0] mem [0:17] = '{8'b10101010,
8'b11111010,
8'b00001010,
8'b00011010,
8'b00101010,
8'b01101010,
8'b10101010,
8'b10101111,
8'b10100000,
8'b10100001,
8'b10100010,
8'b10100111,
8'b10101000,
8'b10101001,
8'b10101010,
8'b10111010,
8'b10001010,
8'b10011010};
assign Data = mem[Address];
	endmodule 
	
	
module Gen_tb;
			reg	[4:0] Address;		
			wire [7:0] Data;
	generateTests  stage(Address,Data);
	initial
		begin	
		Address = 5'b00000 ;  
		repeat(17)
		#5ns Address = Address +1'b1 ;
		#600ns $finish ;
		end  

	endmodule 		
	 
module final_system(clk,go,rst,Address,Data,state_out);
	input clk,go,rst;  
	output  reg [7:0] state_out;
	input  [4:0] Address;
    output  reg [7:0] Data;
	 
	  state_yaz ss	(clk,go,rst,state_out[7:6],state_out[5:4],state_out[3:2],state_out[1:0]);
	 generateTests sa  (Address,Data);
	 always @(posedge clk  or Address )
		 	 if(Data != {state_out[7:6],state_out[5:4],state_out[3:2],state_out[1:0]})
		 $display ("ERROR, Your data does not equal to the true values, in address %b, generator = %b , state out = %b",Address,Data,state_out);
			  else
				  $display("OK, your data matched with the true values, in address %b, generator = %b , state out = %b",Address,Data,state_out);
			  endmodule
			  
	
	
module System_tb;
		 reg  clk,rst,go;
		 reg  [4:0] Address;
		wire [7:0] state_out;
		 wire [7:0] Data; 
		 
	 final_system agag(clk,go,rst,Address,Data,state_out);
			  	initial
			begin
				Address = 5'b00000;
				repeat	(17)
				#5ns Address = 1'b1 + Address;
				end
		initial
			begin
				clk = 0 ;
				rst = 0 ;
				go = 0 ;
				#10ns rst = ~rst;
				#60ns go = 1;
				#200ns $finish ;	
			end
		always #5ns clk = ~clk;
																 
			endmodule 
		
		
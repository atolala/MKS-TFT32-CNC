# MKS-TFT32-CNC
Alternative FW for MKS TFT

!!!!!! The use of this software is done at your own discretion and risk you will be solely responsible for any damage or injury. !!!!!!!


I don't have any source code ! the mod are done with patched firmware only.




1 :
First you need to upload the files to respective SD card.

2 : 
For good use you need to patch smoothieware source code, without this the LCD don't work correctly.


file robot.cpp from smoothie source code find : case 114:{

-- before the line add : 
            case 105:{

                gcode->txt_after_ok.append("T:200 /200 @0 T1:200 /200 @0 B:100 /100 @200");

                return;
            }
 

-- patched M114: :
file robot.cpp from smoothie source code find :
        n = snprintf(buf, sizeof(buf), "C: X:%1.4f Y:%1.4f Z:%1.4f", from_millimeters(std::get<X_AXIS>(pos)), from_millimeters(std::get<Y_AXIS>(pos)), from_millimeters(std::get<Z_AXIS>(pos)));


replace by :

        n = snprintf(buf, sizeof(buf), "C: X:%1.4f Y:%1.4f Z:%1.4f E:0.000", from_millimeters(std::get<X_AXIS>(pos)), from_millimeters(std::get<Y_AXIS>(pos)), from_millimeters(std::get<Z_AXIS>(pos)));




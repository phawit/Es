# Esp8266_SpredSheet
NodeMCU >> Scrip >> SpredSheet
sent data between Esp8266 and GoogleSpreadSheet

1.เริ่มต้น
  -Upload file on nodeMCU << Esp8266_SpredSheet.ino
  -Copy library floder to my library
  -สร้าง Esp8266_SpredSheet.gs ใน GoogleScrip
        Esp8266_SpredSheet ใน SpredSheet
  -ทำตามข้อ 2-4   

2.Esp8266_SpredSheet.ino (NodeMCU)
  -ตั้งค่า macros มาใส่ใน *GScriptId เอามาจาก Data2Sheet.gs (Scrip)
  -ตั้งค่า fingerprint จาก echo | openssl s_client -connect script.google.com:443 |& openssl x509 -fingerprint -noout
  
3.Esp8266_SpredSheet.gs (Scrip)
  -Publish >> Deploy as Web App...>>ตั้งเป็น anyone,even anonomous และ copy macrosURL
   https://script.google.com/macros/s/......................./exec (เอาไปใส่ใน .ino)
  -ตั้งค่าตัวแปร ss 
    //var ss = SpreadsheetApp.openByUrl("https://docs.google.com/spreadsheets/d/....จาก URLSheet......./edit");
    var ss = SpreadsheetApp.openById('1YjlEimTa6MOZJPlojDc7fKnFbjzVC11Wsaj_IcNYx7g');  //จาก URL SpredSheet
    var menu = ss.getSheetByName("Menu");  <ชื่อ Sheet1>
    var sheet = ss.getSheetByName("Data"); <ชื่อ Sheet2>
  -Check connect >>Run>Doget

4.Esp8266_SpredSheet (Sheet)
  -ตั้งชื่อ Sheet1,2 ให้ตรงกับ ตัวแปร ss ("Menu","Data")
  -ตั้งชื่อ หัวข้อ
  
5.On-Off LED ใน C2 ของ Menu(SpredSheet)

  
    

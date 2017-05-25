# Esp8266_SpredSheet
sent data between Esp8266 and GoogleSpreadSheet

NodeMCU >> Scrip >> SpredSheet

1.Data2Sheet.ino (NodeMCU)
  -ตั้งค่า macros มาใส่ใน *GScriptId เอามาจาก Data2Sheet.gs (Scrip)
  -ตั้งค่า fingerprint จาก echo | openssl s_client -connect script.google.com:443 |& openssl x509 -fingerprint -noout

2.Data2Sheet.gs (Scrip)
  -Publish >> Deploy as Web App...>>ตั้งเป็น anyone,even anonomous และ copy macrosURL
   https://script.google.com/macros/s/......................./exec (เอาไปใส่ใน .ino)
  -ตั้งค่าตัวแปร ss 
    //var ss = SpreadsheetApp.openByUrl("https://docs.google.com/spreadsheets/d/....จาก URLSheet......./edit");
    var ss = SpreadsheetApp.openById('1YjlEimTa6MOZJPlojDc7fKnFbjzVC11Wsaj_IcNYx7g');  //จาก URL SpredSheet
    var menu = ss.getSheetByName("Menu");  <ชื่อ Sheet1>
    var sheet = ss.getSheetByName("Data"); <ชื่อ Sheet2>
  -Check connect >>Run>Doget


3.Data2Sheet_res (Sheet)
  -ตั้งชื่อ Sheet1,2 ให้ตรงกับ ตัวแปร ss ("Menu","Data")
  -ตั้งชื่อ หัวข้อ

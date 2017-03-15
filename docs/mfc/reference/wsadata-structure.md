---
title: "WSADATA 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WSADATA"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WSADATA 結構"
ms.assetid: 80cc60e5-f9ae-4290-8ed5-07003136627d
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# WSADATA 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`WSADATA` 結構會儲存視窗通訊端對 `AfxSocketInit` 全域函式的呼叫傳回的初始化資訊。  
  
## 語法  
  
```  
  
      struct WSAData {  
   WORD wVersion;  
   WORD wHighVersion;  
   char szDescription[WSADESCRIPTION_LEN+1];  
   char szSystemStatus[WSASYSSTATUS_LEN+1];  
   unsigned short iMaxSockets;  
   unsigned short iMaxUdpDg;  
   char FAR * lpVendorInfo;  
};  
```  
  
#### 參數  
 *wVersion*  
 Windows Sockets 規格版本 Windows Sockets DLL 要求呼叫端使用。  
  
 *wHighVersion*  
 這個 DLL 可以支援 Windows Sockets 規格版本的 \(也輸入如上所示\)。  通常，這會與 **wVersion**。  
  
 *szDescription*：  
 Windows Sockets DLL 複製 Windows Sockets 實作描述的 Null 終端 ASCII 字串，包括廠商識別。  文字 \(長度 256 個字元\) 可以包含任何字元，不過，廠商會警告物件包含控制項和格式化字元:最可能使用應用程式會將此值是顯示其截斷 \(可能\) 在狀態訊息。  
  
 *szSystemStatus*  
 Windows Sockets DLL 複製相關狀態或組態資訊的 Null 終端 ASCII 字串。  資訊時，才可以使用對使用者或自動化測試\)， Windows Sockets DLL 應該使用這個欄位;不應該視為 **szDescription** 欄位的副檔名。  
  
 *iMaxSockets*  
 單一處理序可能會開啟的通訊端的最大數目。  Windows Sockets 實作可以提供對所有處理序的通訊端設定提供一個全域集區作業;交替，它可以配置通訊端的每個處理序資源。  數字可能很好反映 Windows Sockets DLL 或網路軟體組態的方式。  應用程式撰寫者可以使用這個數字為粗暴指示 Windows Sockets 實作是由應用程式可使用。  例如， X Windows 伺服器可能會檢查 **iMaxSockets** ，當第一次啟動:如果小於 8，應用程式會顯示指出使用者的錯誤訊息重新設定網路軟體。\(這是 **szSystemStatus** 文字可能使用\) 的情況。顯然不保證特定應用程式可能實際配置 **iMaxSockets** 通訊端，，因為可以有其他 Windows Sockets 應用程式在使用中。  
  
 *iMaxUdpDg*  
 大小以支援 Windows Sockets 應用程式傳送或接收最大的使用者資料包通訊協定 \(UDP\) 資料包 \(UDP\) 的位元組。  如果實作不實作限制， **iMaxUdpDg** 為零。  在 Berkeley 通訊端的許多實作，有 8192 位元組一個隱含限制\(必要時會分割\) 的 UDP 資料包。  Windows Sockets 實作可以實作以片段重組緩衝區的配置，例如，限制。  **iMaxUdpDg** 最小值標準 Windows Sockets 實作的是 512。  請注意不論 **iMaxUdpDg**的值，嘗試傳送大於網路的傳輸單元最大值 \(MTU\) 的廣播資料包是不可能的。\(Windows Sockets API 不會提供一個機制尋找 MTU，不過，它必須不小於 512 個位元組\)。  
  
 *lpVendorInfo*  
 至買賣方詳細資料結構的遠端指標。  這個結構的定義 \(如果有提供\) 超出 Windows Sockets 規格的範圍之外。  
  
> [!NOTE]
>  在 MFC 中， `WSADATA` 結構由 `AfxSocketInit` 函式傳回，則呼叫您的 `InitInstance` 函式。  如果您需要之後，使用其資訊可以在程式中擷取結構並儲存它。  
  
## 需求  
 **標頭：**winsock2.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxSocketInit](../Topic/AfxSocketInit.md)
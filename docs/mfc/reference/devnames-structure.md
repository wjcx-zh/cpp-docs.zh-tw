---
title: "DEVNAMES 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEVNAMES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEVNAMES"
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DEVNAMES 結構
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`DEVNAMES` 結構包含可識別驅動程式、裝置和輸出連接埠名稱印表機的字串。  
  
## 語法  
  
```  
  
      typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault;  
    /* driver, device, and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### 參數  
 *wDriverOffset*  
 \(輸入\/輸出\) 以字元為單位指定裝置驅動程式中包含檔名的 NULL 結尾字串的位移 \(不含副檔名\)。  在輸入時，這個字串用來決定這個對話方塊最初顯示的印表機。  
  
 *wDeviceOffset*  
 \(輸入\/輸出\) 以字元為單位指定 null 結尾字串之位移 \(最多 32 個位元組包括 null\) 包含裝置的名稱。  這個字串必須與 [DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565) 結構的 **dmDeviceName** 成員相等。  
  
 *wOutputOffset*  
 \(輸入\/輸出\) 以字元為單位指定包含 DOS 裝置名稱實體輸出媒介 \(輸出連接埠\)的 NULL 結尾字串的位移。  
  
 *wDefault*  
 指定字串是否在 `DEVNAMES` 結構識別包含預設印表機。  這個字串是用來驗證預設印表機自從上次列印作業以來未變更。  在輸入，如果 **DN\_DEFAULTPRN** 旗標已設定， `DEVNAMES` 結構的其他值根據目前預設印表機檢查。  如果任何字串不相符，顯示通知使用者的訊息警告本文可能需要重新格式化。  在輸出時，變更 **wDefault** 成員，只有在列印設定對話方塊出現，而且使用者選取了確定按鈕時。  如果預設印表機已選取，設定 **DN\_DEFAULTPRN** 旗標。  如果特定印表機被選取，旗標未設定。  在這個成員的其他位元會保留給內部由列印對話方塊程序使用。  
  
## 備註  
 **PrintDlg** 函式使用這些字串初始化系統定義的列印對話方塊的成員。  當使用者關閉對話方塊時，所選取之印表機的資訊傳回此結構中。  
  
## 需求  
 **Header:** commdlg.h  
  
## 請參閱  
 [結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../Topic/CPrintDialog::CreatePrinterDC.md)
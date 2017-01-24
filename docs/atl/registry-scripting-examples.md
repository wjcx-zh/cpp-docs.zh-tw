---
title: "Registry Scripting Examples | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "registrar scripts [ATL]"
  - "登錄, Registrar"
  - "指令碼, 範例"
  - "指令碼, Registrar scripts"
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Registry Scripting Examples
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題中的指令碼的範例示範如何將機碼加入至系統登錄，註冊 COM 伺服器管理員，，並指定多個剖析樹狀結構。  
  
## 將索引鍵到 HKEY\_CURRENT\_USER  
 下列剖析樹狀結構說明將單一索引鍵加入到系統登錄的簡單的指令碼。  特別是，指令碼加入索引鍵， `MyVeryOwnKey`，加入 `HKEY_CURRENT_USER`。  它也會產生 `HowGoesIt?` 的預設字串值給新機碼:  
  
```  
HKEY_CURRENT_USER  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
```  
  
 這個指令碼可以很容易地擴充定義多個子機碼如下:  
  
```  
HKCU  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
   {  
      'HasASubkey'  
      {  
         'PrettyCool?' = d '55'  
         val 'ANameValue' = s 'WithANamedValue'  
      }  
   }  
}  
```  
  
 現在，指令碼加入子機碼， `HasASubkey`，加入 `MyVeryOwnKey`。  為這個子機碼，它將 `PrettyCool?` 子機碼 \(使用預設 `DWORD` 值為 55\) 和 \(名稱為\) 的 `ANameValue` 值 \(具有 `WithANamedValue`的字串值\)。  
  
##  <a name="_atl_register_the_registrar_com_server"></a> 註冊 COM 伺服器管理員  
 下列指令碼管理員註冊 COM 伺服器。  
  
```  
HKCR  
{  
   ATL.Registrar = s 'ATL Registrar Class'  
   {  
      CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'  
   }  
   NoRemove CLSID  
   {  
      ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} =  
                   s 'ATL Registrar Class'  
      {  
         ProgID = s 'ATL.Registrar'  
         InprocServer32 = s '%MODULE%'  
         {  
            val ThreadingModel = s 'Apartment'  
         }  
      }  
   }  
}  
```  
  
 在執行階段，這個剖析樹狀結構將 `ATL.Registrar` 索引鍵加入 `HKEY_CLASSES_ROOT`。  為這個新的金鑰，然後:  
  
-   指定 `ATL Registrar Class` ，索引鍵的預設字串值。  
  
-   將 `CLSID` 做為子機碼。  
  
-   為指定 `CLSID``{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 。  \(這個值是管理員的 CLSID 來與 `CoCreateInstance`的使用\)。  
  
 因為 `CLSID` 共用，以移除模式不應該將它移除。  陳述式， `NoRemove CLSID`，以指出可以在暫存器模式應該開啟並忽略 `CLSID` 在 PWA 模式。  
  
 `ForceRemove` 陳述式將會移除索引鍵和所有提供環境維護函式及其子機碼中重新建立索引鍵前面。  如果子機碼的名稱已變更，這會很有用。  在這個指令碼的範例中， `ForceRemove` 檢查 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 是否已經存在。  如果是， `ForceRemove`:  
  
-   遞迴地刪除 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}` 和其所有子機碼。  
  
-   重新建立 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  
  
-   將 `ATL Registrar Class` ， `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`的預設字串值。  
  
 剖析樹狀結構會加入兩個新的子機碼至 `{44EC053A-400F-11D0-9DCD-00A0C90391D3}`。  第一個索引鍵， `ProgID`，取得 ProgID 的預設字串值。  第二個索引鍵， `InprocServer32`，取得預設字串值， `%MODULE%`，就是一節中說明的前置處理器值， [使用可取代的參數 \(管理員的前置處理器\)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)，本文。  `InprocServer32` 也取得具名值， `ThreadingModel`，與 `Apartment`的字串值。  
  
## 指定多個剖析樹狀結構  
 若要指定多個指令碼中剖析樹狀結構，將樹狀結構中的結尾。  例如，下列指令碼加入索引鍵， `MyVeryOwnKey`，加入 `HKEY_CLASSES_ROOT` 和 `HKEY_CURRENT_USER`的剖析樹狀結構:  
  
```  
HKCR  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
HKEY_CURRENT_USER  
{  
   'MyVeryOwnKey' = s 'HowGoesIt?'  
}  
```  
  
> [!NOTE]
>  在登錄器指令碼， 4K 最大語彙基元大小。  \(語彙基元是語法的任何可辨識的項目\)。在上一個指令碼的範例中， `HKCR`、 `HKEY_CURRENT_USER`、 `'MyVeryOwnKey'`和 `'HowGoesIt?'` 是所有語彙基元。  
  
## 請參閱  
 [Creating Registrar Scripts](../atl/creating-registrar-scripts.md)
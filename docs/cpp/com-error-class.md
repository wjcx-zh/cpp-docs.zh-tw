---
title: "_com_error 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_error"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_com_error 類別"
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# _com_error 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 專有的**  
  
 `_com_error` 物件代表標頭檔的錯誤處理包裝函式偵測到的一個例外狀況，其為型別程式庫或 COM 支援類別之一所產生。  `_com_error` 類別會封裝 `HRESULT` 錯誤碼和任何相關聯的 `IErrorInfo Interface` 物件。  
  
### 建構  
  
|||  
|-|-|  
|[\_com\_error](../cpp/com-error-com-error.md)|建構 `_com_error` 物件。|  
  
### 運算子  
  
|||  
|-|-|  
|[operator \=](../cpp/com-error-operator-equal.md)|將現有的 `_com_error` 物件指派給另一個。|  
  
### 擷取器函式  
  
|||  
|-|-|  
|[錯誤](../cpp/com-error-error.md)|擷取傳給建構函式的 `HRESULT`。|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|擷取傳給建構函式的 `IErrorInfo` 物件。|  
|[WCode](../cpp/com-error-wcode.md)|擷取對應至封裝的 `HRESULT` 之 16 位元錯誤碼。|  
  
### IErrorInfo 函式  
  
|||  
|-|-|  
|[描述](../cpp/com-error-description.md)|呼叫 `IErrorInfo::GetDescription` 函式。|  
|[HelpContext](../cpp/com-error-helpcontext.md)|呼叫 `IErrorInfo::GetHelpContext` 函式。|  
|[HelpFile](../cpp/com-error-helpfile.md)|呼叫 `IErrorInfo::GetHelpFile` 函式|  
|[來源](../cpp/com-error-source.md)|呼叫 `IErrorInfo::GetSource` 函式。|  
|[GUID](../cpp/com-error-guid.md)|呼叫 `IErrorInfo::GetGUID` 函式。|  
  
### 格式訊息擷取器  
  
|||  
|-|-|  
|[ErrorMessage](../cpp/com-error-errormessage.md)|擷取儲存於 `_com_error` 物件中的 HRESULT 的字串訊息。|  
  
### 對 HRESULT 對應程式的 ExepInfo.wCode  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|將 32 位元的 `HRESULT` 對應至 16 位元的 `wCode`。|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|將 16 位元的 `wCode` 對應至 32 位元的 `HRESULT`。|  
  
## END Microsoft 專有  
  
## 需求  
 `Header:` comdef.h  
  
 `Lib:` comsuppw.lib 或 comsuppwd.lib \(如需詳細資訊，請參閱 [\/Zc:wchar\_t \(wchar\_t 是原生類型\)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)\)  
  
## 請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo Interface](http://msdn.microsoft.com/zh-tw/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)
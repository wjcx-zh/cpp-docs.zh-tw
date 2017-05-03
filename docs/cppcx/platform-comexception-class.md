---
title: "Platform::COMException 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/30/2016"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Platform/Platform::COMException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Platform::COMException 類別"
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 4
---
# Platform::COMException 類別
代表應用程式執行期間所發生的 COM 錯誤。 COMException 是一組預先定義的標準例外狀況所適用的基底類別。  
  
## 語法  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
## Members  
 COMException 類別繼承自 Object 類別以及 IException、IPrintable 與 IEquatable 介面。  
  
 COMException 也有下列型別的成員。  
  
 **建構函式**  
  
|成員|描述|  
|--------|--------|  
|`COMException`|初始化 COMException 類別的新執行個體。|  
  
 **方法**  
  
 COMException 類別會從 [Platform::Object 類別](../cppcx/platform-object-class.md) 繼承 Equals\(\)、Finalize\(\)、GetHashCode\(\)、GetType\(\)、MemberwiseClose\(\) 與 ToString\(\) 等方法。  
  
 **屬性**  
  
 COMException 類別具有下列屬性。  
  
|成員|描述|  
|--------|--------|  
|[Exception::HResult 屬性](../cppcx/exception-hresult-property.md)|對應於例外狀況的 HRESULT。|  
|[Exception::Message 屬性](../cppcx/exception-message-property.md)|說明例外狀況的訊息。|  
  
## 衍生的例外狀況  
 下列預先定義的例外狀況衍生自 COMException。 它們與 COMException 的差異，僅在於其名稱、其建構函式的名稱以及其基礎 HRESULT 值。  
  
|名稱|基礎 HRESULT|描述|  
|--------|----------------|--------|  
|COMException|*使用者定義的 HRESULT*|在 COM 方法呼叫傳回無法辨認的 HRESULT 時擲回。|  
|AccessDeniedException|E\_ACCESSDENIED|在存取資源或功能遭拒時擲回。|  
|ChangedStateException|E\_CHANGED\_STATE|在父集合變更後呼叫集合 Iterator 或集合檢視的方法時擲回，藉以讓該方法的結果失效。|  
|ClassNotRegisteredException|REGDB\_E\_CLASSNOTREG|在 COM 類別未登錄時擲回。|  
|DisconnectedException|RPC\_E\_DISCONNECTED|在物件與用戶端的連接中斷時擲回。|  
|FailureException|E\_FAIL|在作業失敗時擲回。|  
|InvalidArgumentException|E\_INVALIDARG|當其中一個提供給方法的引數無效時擲回。|  
|InvalidCastException|E\_NOINTERFACE|在類型無法轉換成另一種類型時擲回。|  
|NotImplementedException|E\_NOTIMPL|在介面方法未於類別上實作時擲回。|  
|NullReferenceException|E\_POINTER|在嘗試解除 Null 物件的參考時擲回。|  
|OperationCanceledException|E\_ABORT|在作業中止時擲回。|  
|OutOfBoundsException|E\_BOUNDS|在作業嘗試存取有效範圍以外的資料時擲回。|  
|OutOfMemoryException|E\_OUTOFMEMORY|在沒有足夠的記憶體可完成作業時擲回。|  
  
## 需求  
 **最低支援用戶端：** [!INCLUDE[win8](../cppcx/includes/win8-md.md)]  
  
 **最低支援伺服器：** [!INCLUDE[winserver8](../cppcx/includes/winserver8-md.md)]  
  
 **命名空間：**Platform  
  
 **中繼資料：**platform.winmd  
  
## 請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)
---
title: 'Platform:: comexception 類別 |Microsoft Docs'
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
dev_langs:
- C++
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ef60fc542b38c7619ce7b65cc7f39db79ed1b228
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764107"
---
# <a name="platformcomexception-class"></a>Platform::COMException 類別
代表應用程式執行期間所發生的 COM 錯誤。 COMException 是一組預先定義的標準例外狀況所適用的基底類別。  
  
## <a name="syntax"></a>語法  
  
```cpp  
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable  
```  
  
### <a name="members"></a>成員  
 COMException 類別繼承自 Object 類別以及 IException、IPrintable 與 IEquatable 介面。  
  
 COMException 也有下列型別的成員。  
  
 **建構函式**  
  
|成員|描述|  
|------------|-----------------|  
|[COMException](#ctor)|初始化 COMException 類別的新執行個體。|  
  
 **方法**  
  
 COMException 類別會從 [Platform::Object Class](../cppcx/platform-object-class.md)繼承 Equals()、Finalize()、GetHashCode()、GetType()、MemberwiseClose() 與 ToString() 等方法。  
  
 **屬性**  
  
 COMException 類別具有下列屬性。  
  
|成員|描述|  
|------------|-----------------|  
|[Exception::HResult](#hresult)|對應於例外狀況的 HRESULT。|  
|[Exception::Message](#message)|說明例外狀況的訊息。|  
  
## <a name="derived-exceptions"></a>衍生的例外狀況  
 下列預先定義的例外狀況衍生自 COMException。 它們與 COMException 的差異，僅在於其名稱、其建構函式的名稱以及其基礎 HRESULT 值。  
  
|名稱|基礎 HRESULT|描述|  
|----------|------------------------|-----------------|  
|COMException|*使用者定義的 HRESULT*|在 COM 方法呼叫傳回無法辨認的 HRESULT 時擲回。|  
|AccessDeniedException|E_ACCESSDENIED|在存取資源或功能遭拒時擲回。|  
|ChangedStateException|E_CHANGED_STATE|在父集合變更後呼叫集合 Iterator 或集合檢視的方法時擲回，藉以讓該方法的結果失效。|  
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|在 COM 類別未登錄時擲回。|  
|DisconnectedException|RPC_E_DISCONNECTED|在物件與用戶端的連接中斷時擲回。|  
|FailureException|E_FAIL|在作業失敗時擲回。|  
|InvalidArgumentException|E_INVALIDARG|當其中一個提供給方法的引數無效時擲回。|  
|InvalidCastException|E_NOINTERFACE|在類型無法轉換成另一種類型時擲回。|  
|NotImplementedException|E_NOTIMPL|在介面方法未於類別上實作時擲回。|  
|NullReferenceException|E_POINTER|在嘗試解除 Null 物件的參考時擲回。|  
|OperationCanceledException|E_ABORT|在作業中止時擲回。|  
|OutOfBoundsException|E_BOUNDS|在作業嘗試存取有效範圍以外的資料時擲回。|  
|OutOfMemoryException|E_OUTOFMEMORY|在沒有足夠的記憶體可完成作業時擲回。|  
  
### <a name="requirements"></a>需求  
 **最低支援用戶端：** Windows 8  
  
 **最低支援伺服器：** Windows Server 2012  
  
 **命名空間：** Platform  
  
 **中繼資料：** platform.winmd  

## <a name="ctor"></a> Comexception:: Comexception 建構函式
初始化 COMException 類別的新執行個體。  
  
### <a name="syntax"></a>語法  
  
```cpp  
COMException( int hresult )  
```  
  
### <a name="parameters"></a>參數  
 hresult  
 由例外狀況表示的錯誤 HRESULT。  
  


## <a name="hresult"></a> Comexception:: Hresult 屬性
對應於例外狀況的 HRESULT。  
  
### <a name="syntax"></a>語法  
  
```cpp  
public:property int HResult {    int get();}  
```  
  
## <a name="property-value"></a>屬性值  
 指定錯誤的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 如需如何解譯 HRESULT 值的詳細資訊，請參閱[錯誤碼的結構 COM](/windows/desktop/com/structure-of-com-error-codes)。  

## <a name="message"></a> Comexception:: Message 屬性
說明例外狀況的訊息。  
  
### <a name="syntax"></a>語法  
  
```cpp  
public:property String^ Message {    String^ get();}  
```  
  
### <a name="property-value"></a>屬性值  
 例外狀況的描述。  
    

## <a name="see-also"></a>另請參閱  
 [Platform 命名空間](../cppcx/platform-namespace-c-cx.md)
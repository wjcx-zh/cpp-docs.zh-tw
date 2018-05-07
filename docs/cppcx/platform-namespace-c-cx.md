---
title: Platform 命名空間 (C + + /CX) |Microsoft 文件
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- Platform/Platform
dev_langs:
- C++
helpviewer_keywords:
- Platform Namespace (C++/CX)
ms.assetid: b160e822-d424-43d2-ba60-57b0e81f259c
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 348bedcde953cbcd6084023d6f7117c7f7f001f5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="platform-namespace-ccx"></a>Platform 命名空間 (C++/CX)
包含與 Windows 執行階段相容的內建類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
using namespace Platform;  
```  
  
### <a name="members"></a>成員  
 **屬性**  
  
 Platform 命名空間包含屬性、類別、列舉、介面和結構。 Platform 也包含巢狀命名空間。  
  
|屬性|描述|  
|---------------|-----------------|  
|旗標|指出可將列舉視為位元欄位，也就是一組旗標。|  
|MTAThread|指出應用程式的執行緒模型為多執行緒 Apartment (MTA)。|  
|STAThread|指出應用程式的執行緒模型為單一執行緒 Apartment (STA)。|  
  
 **類別**  
  
 Platform 命名空間具有下列類別。  
  
|類別|描述|  
|-----------|-----------------|  
|[Platform::AccessDeniedException 類別](../cppcx/platform-accessdeniedexception-class.md)|當存取拒絕資源或功能時引發。|  
|[Platform::Agile 類別](../cppcx/platform-agile-class.md)|以 Agile 物件表示非 Agile 物件。|  
|[Platform::Array 類別](../cppcx/platform-array-class.md)|表示可修改的一維陣列。|  
|[Platform:: arrayreference 類別](../cppcx/platform-arrayreference-class.md)|表示一個陣列，此陣列的初始化已最佳化，可讓複製作業減至最少。|  
|[Platform::Box 類別](../cppcx/platform-box-class.md)|用來宣告 Boxed 類型，該類型會在橫跨應用程式二進位介面 (ABI) 進行傳遞或儲存在 [Platform::Object^](../cppcx/platform-object-class.md)類型的變數中時，封裝類似 Windows::Foundation::DateTime 或 int64 的實值類型。|  
|[Platform::ChangedStateException 類別](../cppcx/platform-changedstateexception-class.md)|在父集合變更後呼叫集合 Iterator 或集合檢視的方法時擲回，藉以讓該方法的結果失效。|  
|[Platform:: classnotregisteredexception 類別](../cppcx/platform-classnotregisteredexception-class.md)|在 COM 類別未登錄時擲回。|  
|[Platform::COMException 類別](../cppcx/platform-comexception-class.md)|代表當 COM 方法呼叫傳回無法辨認的值時所擲回的例外狀況。|  
|[Platform::Delegate 類別](../cppcx/platform-delegate-class.md)|代表回呼函式的簽章。|  
|[Platform::DisconnectedException 類別](../cppcx/platform-disconnectedexception-class.md)|物件與用戶端已中斷連接。|  
|[Platform::Exception 類別](../cppcx/platform-exception-class.md)|代表應用程式執行期間所發生的錯誤。 例外狀況的基底類別。|  
|[Platform::FailureException 類別](../cppcx/platform-failureexception-class.md)|作業失敗時擲回。 這是 E_FAIL HRESULT 的對等用法。|  
|[Platform::Guid 實值類別](../cppcx/platform-guid-value-class.md)|表示 Windows 執行階段類型系統中的 GUID。|  
|[Platform::InvalidArgumentException 類別](../cppcx/platform-invalidargumentexception-class.md)|當其中一個提供給方法的引數無效時擲回。|  
|[Platform::InvalidCastException 類別](../cppcx/platform-invalidcastexception-class.md)|在無效轉型或明確轉換時擲回。|  
|[Platform::MTAThreadAttribute 類別](../cppcx/platform-mtathreadattribute-class.md)|指出應用程式的執行緒模型為多執行緒 Apartment (MTA)。|  
|[Platform::NotImplementedException 類別](../cppcx/platform-notimplementedexception-class.md)|在介面方法未於類別上實作時擲回。|  
|[Platform::NullReferenceException 類別](../cppcx/platform-nullreferenceexception-class.md)|在嘗試解除 Null 物件的參考時擲回。|  
|[Platform::Object 類別](../cppcx/platform-object-class.md)|提供通用行為的基底類別。|  
|[Platform::ObjectDisposedException 類別](../cppcx/platform-objectdisposedexception-class.md)|在已處置的物件上執行作業時擲回。|  
|[Platform::OperationCanceledException 類別](../cppcx/platform-operationcanceledexception-class.md)|在作業中止時擲回。|  
|[Platform:: outofboundsexception 類別](../cppcx/platform-outofboundsexception-class.md)|在作業嘗試存取有效範圍以外的資料時擲回。|  
|[Platform::OutOfMemoryException 類別](../cppcx/platform-outofmemoryexception-class.md)|在沒有足夠的記憶體可完成作業時擲回。|  
|[Platform::STAThreadAttribute 類別](../cppcx/platform-stathreadattribute-class.md)|指出應用程式的執行緒模型為單一執行緒 Apartment (STA)。|  
|[Platform::String 類別](../cppcx/platform-string-class.md)|用來代表文字的 Unicode 字元的循序集合。|  
|[Platform::StringReference 類別](../cppcx/platform-stringreference-class.md)|可以在產生最少複製負荷的情況下，存取字串緩衝區。|  
|[Platform::Type 類別](../cppcx/platform-type-class.md)|依分類列舉來識別內建類型。|  
|[Platform::ValueType 類別](../cppcx/platform-valuetype-class.md)|實值類型執行個體的基底類別。|  
|[Platform:: weakreference 類別](../cppcx/platform-weakreference-class.md)|提供不會遞增參考計數之 ref 類別物件的弱式參考。|  
|[Platform:: writeonlyarray 類別](../cppcx/platform-writeonlyarray-class.md)|表示一維的唯寫陣列，這個陣列可做為實作 FillArray 模式之方法的輸入參數。|  
|[Platform::WrongThreadException 類別](../cppcx/platform-wrongthreadexception-class.md)|在執行緒透過不屬於其 Apartment 之 Proxy 物件的介面指標進行呼叫時擲回。|  
  
 **介面實作**  
  
 Platform 命名空間會定義下列介面。  
  
|介面|描述|  
|---------------|-----------------|  
|[Platform::IBox 介面](../cppcx/platform-ibox-interface.md)|用來將實值類型傳遞給函式，該函式的參數類型為 Platform::Object^。|  
|[Platform::IBoxArray 介面](../cppcx/platform-iboxarray-interface.md)|用來將實值類型的陣列傳遞給函式的介面，該函式的參數類型為 Platform::Array。|  
|[Platform::IDisposable 介面](../cppcx/platform-idisposable-interface.md)|用來釋放 Unmanaged 資源。|  
  
 **列舉**  
  
 Platform 命名空間具有以下列舉。  
  
|介面|描述|  
|---------------|-----------------|  
|[Platform::CallbackContext 列舉](../cppcx/platform-callbackcontext-enumeration.md)|用來做為委派建構函式參數的列舉。 它會判斷回呼是否要封送處理到來源執行緒或呼叫端執行緒。|  
|[Platform:: typecode 列舉](../cppcx/platform-typecode-enumeration.md)|指定代表內建類型的數值分類。|  
  
 **結構**  
  
 Platform 命名空間具有下列結構。  
  
|結構|描述|  
|---------------|-----------------|  
|[Platform::Enum 類別](../cppcx/platform-enum-class.md)|表示具名常數。|  
|[Platform::Guid 實值類別](../cppcx/platform-guid-value-class.md)|代表 GUID。|  
|[Platform::IntPtr 實值類別](../cppcx/platform-intptr-value-class.md)|大小適用於平台的帶正負號的指標 (32 位元或 64 位元)。|  
|[Platform::SizeT 實值類別](../cppcx/platform-sizet-value-class.md)|用來表示物件大小的不帶正負號的資料類型。|  
|[Platform::UIntPtr 實值類別](../cppcx/platform-uintptr-value-class.md)|大小適用於平台的不帶正負號的指標 (32 位元或 64 位元)。|  
  
## <a name="see-also"></a>另請參閱  
 [Platform:: collections 命名空間](../cppcx/platform-collections-namespace.md)   
 [Platform::Runtime::CompilerServices 命名空間](../cppcx/platform-runtime-compilerservices-namespace.md)   
 [Platform::Runtime::InteropServices 命名空間](../cppcx/platform-runtime-interopservices-namespace.md)   
 [Platform::Metadata 命名空間](../cppcx/platform-metadata-namespace.md)
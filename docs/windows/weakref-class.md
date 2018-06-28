---
title: WeakRef 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba7efc595be55b807cd3f044269db0debcb72407
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891694"
---
# <a name="weakref-class"></a>WeakRef 類別
代表 *弱式參考* 僅供 Windows 執行階段使用，而不供傳統 COM 使用。 弱式參考代表不一定可存取的物件。  
  
## <a name="syntax"></a>語法  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>備註  
 WeakRef 物件會維護 *強式參考*，它與物件相關聯，可以是有效的或無效的。 呼叫 As() 或 AsIID() 方法，以取得強式參考。 當強式參考為有效時，它可以存取相關聯的物件。 強式參考無效時 (`nullptr`)，就無法存取相關聯的物件。  
  
 WeakRef 物件通常用以表示由外部執行緒或應用程式控制其存在的物件。 例如，將 WeakRef 物件從參考建構成檔案物件。 在檔案開啟時，強式參考是有效的。 但若檔案關閉，強式參考就變成無效的。  
  
 請注意，在 Windows 10 SDK 的 [As](../windows/weakref-as-method.md)、 [AsIID](../windows/weakref-asiid-method.md) 和 [CopyTo](../windows/weakref-copyto-method.md) 方法中有行為變更。 先前，在呼叫上述任一方法之後，您可以檢查 WeakRef 有無 `nullptr` 來判斷是否已成功取得強式參考，如下列程式碼所示：  
  
```cpp  
WeakRef wr;  
strongComptrRef.AsWeak(&wr);  
  
// Now suppose that the object strongComPtrRef points to no longer exists  
// and the following code tries to get a strong ref from the weak ref:  
ComPtr<ISomeInterface> strongRef;  
HRESULT hr = wr.As(&strongRef);  
  
// This check won't work with the Windows 10 SDK version of the library.  
// Check the input pointer instead.  
if(wr == nullptr)  
{  
    wprintf(L"Couldn’t get strong ref!");  
}  
  
```  
  
 使用 Windows 10 SDK (或更新版本) 時，上述程式碼不作用。 相反地，請檢查傳入的指標`nullptr`。  
  
```cpp  
if (strongRef == nullptr)  
{  
    wprintf(L"Couldn't get strong ref!");  
 }  
  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakRef::WeakRef 建構函式](../windows/weakref-weakref-constructor.md)|初始化 WeakRef 類別的新執行個體。|  
|[WeakRef::~WeakRef 解構函式](../windows/weakref-tilde-weakref-destructor.md)|取消初始化 WeakRef 類別目前的執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakRef::As 方法](../windows/weakref-as-method.md)|設定指定的 ComPtr 指標參數代表指定的介面。|  
|[WeakRef::AsIID 方法](../windows/weakref-asiid-method.md)|設定指定的 ComPtr 指標參數，以代表指定的介面識別碼。|  
|[WeakRef::CopyTo 方法](../windows/weakref-copyto-method.md)|指派介面指標 (如有提供) 給指定的指標變數。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[WeakRef::operator& 運算子](../windows/weakref-operator-ampersand-operator.md)|傳回表示目前 WeakRef 物件的 ComPtrRef 物件。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)
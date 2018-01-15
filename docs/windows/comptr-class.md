---
title: "ComPtr 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr
dev_langs: C++
helpviewer_keywords: ComPtr class
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 04f8181c7308d63cc4fe07aaf4a05d34ccfaf132
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="comptr-class"></a>ComPtr 類別
建立代表範本參數所指定之介面的 *「智慧型指標」* (Smart Pointer) 類型。 ComPtr 自動維護基礎介面指標的參考計數，並在參考計數歸零時釋放介面。  
  
## <a name="syntax"></a>語法  
  
```  
template <  
   typename T  
>  
class ComPtr;  
  
template<  
   class U  
>  
friend class ComPtr;  
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 ComPtr 代表的介面。  
  
 `U`  
 與目前 ComPtr 為 Friend 的類別 (使用這個參數的範本會受到保護)。  
  
## <a name="remarks"></a>備註  
 ComPtr<> 宣告一個代表基礎介面指標的類型。 使用 comptr<> 來宣告一個變數，然後使用箭號成員存取運算子 (`->`) 來存取介面成員函式。  
  
 如需智慧型指標的詳細資訊，請參閱 MSDN Library 中 [COM Coding Practices](http://msdn.microsoft.com/en-us/76aca556-b4d6-4e67-a2a3-4439900f0c39)主題的＜COM 智慧型指標＞一節。  
  
## <a name="members"></a>成員  
  
### <a name="public-typedefs"></a>公用 Typedefs  
  
|名稱|描述|  
|----------|-----------------|  
|`InterfaceType`|`T` 範本參數所指定之類型的同義字。|  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtr::ComPtr 建構函式](../windows/comptr-comptr-constructor.md)|初始化 ComPtr 類別的新執行個體。 多載提供預設、複製、移動和轉換建構函式。|  
|[ComPtr::~ComPtr 解構函式](../windows/comptr-tilde-comptr-destructor.md)|取消初始化 ComPtr 的執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtr::As 方法](../windows/comptr-as-method.md)|傳回 ComPtr 物件，代表指定範本參數所識別的介面。|  
|[ComPtr::AsIID 方法](../windows/comptr-asiid-method.md)|傳回 ComPtr 物件，代表指定介面 ID 所識別的介面。|  
|[ComPtr::AsWeak 方法](../windows/comptr-asweak-method.md)|擷取目前物件的弱式參考。|  
|[ComPtr::Attach 方法](../windows/comptr-attach-method.md)|將這個 ComPtr 與目前範本類型參數所指定的介面類型產生關聯。|  
|[ComPtr::CopyTo 方法](../windows/comptr-copyto-method.md)|將與這個 ComPtr 相關聯的目前或指定介面，複製到指定的輸出指標。|  
|[ComPtr::Detach 方法](../windows/comptr-detach-method.md)|將這個 ComPtr 與其所代表的介面取消關聯。|  
|[ComPtr::Get 方法](../windows/comptr-get-method.md)|擷取與這個 ComPtr 相關聯之介面的指標。|  
|[ComPtr::GetAddressOf 方法](../windows/comptr-getaddressof-method.md)|擷取 [ptr_](../windows/comptr-ptr-data-member.md) 資料成員的位址，其中包含這個 ComPtr 所代表之介面的指標。|  
|[ComPtr::ReleaseAndGetAddressOf 方法](../windows/comptr-releaseandgetaddressof-method.md)|釋放與這個 ComPtr 相關聯的介面，然後擷取 [ptr_](../windows/comptr-ptr-data-member.md) 資料成員的位址，其中包含已釋放之介面的指標。|  
|[ComPtr::Reset](../windows/comptr-reset.md)|釋放與這個 ComPtr 相關聯的介面指標的所有參考。|  
|[ComPtr::Swap 方法](../windows/comptr-swap-method.md)|將受目前 ComPtr 管理的介面，與受指定 ComPtr 管理的介面互相交換。|  
  
### <a name="protected-methods"></a>受保護的方法  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtr::InternalAddRef 方法](../windows/comptr-internaladdref-method.md)|遞增與這個 ComPtr 相關聯之介面的參考計數。|  
|[ComPtr::InternalRelease 方法](../windows/comptr-internalrelease-method.md)|在與這個 ComPtr 相關聯的介面上，執行 COM 釋放作業。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtr::operator Microsoft::WRL::Details::BoolType 運算子](../windows/comptr-operator-microsoft-wrl-details-booltype-operator.md)|表示 ComPtr 是否正在管理介面的物件存留期。|  
|[ComPtr::operator& 運算子](../windows/comptr-operator-ampersand-operator.md)|擷取目前 ComPtr 的位址。|  
|[ComPtr::operator= 運算子](../windows/comptr-operator-assign-operator.md)|將值指派給目前的 ComPtr。|  
|[ComPtr::operator-> 運算子](../windows/comptr-operator-arrow-operator.md)|擷取目前範本參數所指定之類型的指標。|  
|[ComPtr::operator== 運算子](../windows/comptr-operator-equality-operator.md)|表示兩個 ComPtr 物件是否相等。|  
|[ComPtr::operator!= 運算子](../windows/comptr-operator-inequality-operator.md)|表示兩個 ComPtr 物件是否不相等。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[ComPtr::ptr_ 資料成員](../windows/comptr-ptr-data-member.md)|包含與這個 ComPtr 相關聯並受其管理之介面的指標。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `ComPtr`  
  
## <a name="requirements"></a>需求  
 **標頭：** client.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)
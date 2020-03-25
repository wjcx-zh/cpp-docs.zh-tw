---
title: CreateClassFactory 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateClassFactory
helpviewer_keywords:
- CreateClassFactory function
ms.assetid: 772d5d1b-8872-4745-81ca-521a39564713
ms.openlocfilehash: 0467a9a1341e29a61a3b32d999769b01385f641f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214054"
---
# <a name="createclassfactory-function"></a>CreateClassFactory 函式

建立會產生指定類別之執行個體的處理站。

## <a name="syntax"></a>語法

```cpp
template<typename Factory>
inline HRESULT STDMETHODCALLTYPE CreateClassFactory(
   _In_ unsigned int *flags,
   _In_ const CreatorMap* entry,
   REFIID riid,
   _Outptr_ IUnknown **ppFactory
) throw();
```

### <a name="parameters"></a>參數

*flags*<br/>
一或多個[RuntimeClassType](runtimeclasstype-enumeration.md)列舉值的組合。

*entry*<br/>
[CreatorMap](creatormap-structure.md)的指標，其中包含參數*riid*的初始化和註冊資訊。

*riid*<br/>
介面識別碼的參考。

*ppFactory*<br/>
如果此作業成功完成，則為 Class Factory 的指標。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如果範本參數*Factory*不是衍生自介面 `IClassFactory`，就會發出判斷提示錯誤。

## <a name="requirements"></a>需求

**標頭：** module. h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers::Details 命名空間](microsoft-wrl-wrappers-details-namespace.md)

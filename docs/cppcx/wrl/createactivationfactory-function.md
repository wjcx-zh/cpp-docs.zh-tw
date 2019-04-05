---
title: CreateActivationFactory 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreateActivationFactory
helpviewer_keywords:
- CreateActivationFactory function
ms.assetid: a1a53e04-6757-4faf-a4c8-ecf06e43b959
ms.openlocfilehash: ca3469128cf3d412138d5d39a1587cbc20150699
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59040602"
---
# <a name="createactivationfactory-function"></a>CreateActivationFactory 函式

建立會產生指定類別之執行個體 (由 Windows 執行階段啟動) 的處理站。

## <a name="syntax"></a>語法

```cpp
template<typename Factory>
   inline HRESULT STDMETHODCALLTYPE CreateActivationFactory(
      _In_ unsigned int *flags,        _In_ const CreatorMap* entry,
      REFIID riid,
   _Outptr_ IUnknown **ppFactory) throw();
```

### <a name="parameters"></a>參數

*旗標*<br/>
一或多個組合[RuntimeClassType](runtimeclasstype-enumeration.md)列舉值。

*entry*<br/>
指標[CreatorMap](creatormap-structure.md) ，其中包含參數的初始設定和註冊資訊*riid*。

*riid*<br/>
參考介面識別碼。

*ppFactory*<br/>
如果這項作業成功完成啟動處理站的指標。

## <a name="return-value"></a>傳回值

如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="remarks"></a>備註

如果，就會發出判斷提示錯誤範本參數*Factory*不是衍生自介面`IActivationFactory`。

## <a name="requirements"></a>需求

**標頭：** module.h

**命名空間：** Microsoft:: wrl

## <a name="see-also"></a>另請參閱

[Microsoft::WRL::Wrappers::Details 命名空間](microsoft-wrl-wrappers-details-namespace.md)
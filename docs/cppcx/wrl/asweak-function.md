---
title: AsWeak 函式
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::AsWeak
helpviewer_keywords:
- AsWeak function
ms.assetid: a6f10cfc-c1d6-4761-adb9-1a119cc99913
ms.openlocfilehash: d11f55d57f4053fd6d46b727a8ed91b340d1764b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214171"
---
# <a name="asweak-function"></a>AsWeak 函式

擷取指定執行個體的弱式參考。

## <a name="syntax"></a>語法

```cpp
template<typename T>
HRESULT AsWeak(
   _In_ T* p,
   _Out_ WeakRef* pWeak
);
```

### <a name="parameters"></a>參數

*T*<br/>
參數*p*類型的指標。

*p*<br/>
類型的實例。

*pWeak*<br/>
當此作業完成時，為參數*p*的弱式參考的指標。

## <a name="return-value"></a>傳回值

S_OK，如果此操作成功，則為，否則，就是指出失敗原因的錯誤 HRESULT。

## <a name="requirements"></a>需求

**標頭：** client.h

**命名空間：** Microsoft::WRL

## <a name="see-also"></a>另請參閱

[Microsoft::WRL 命名空間](microsoft-wrl-namespace.md)

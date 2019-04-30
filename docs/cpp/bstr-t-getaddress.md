---
title: _bstr_t::GetAddress
ms.date: 11/04/2016
f1_keywords:
- _bstr_t::GetAddress
helpviewer_keywords:
- GetAddress method [C++]
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
ms.openlocfilehash: 4d51539d2afbb2fbcc860b6c4d821df119aca418
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393892"
---
# <a name="bstrtgetaddress"></a>_bstr_t::GetAddress

**Microsoft 專屬**

釋放任何現有字串並傳回新配置字串的位址。

## <a name="syntax"></a>語法

```
BSTR* GetAddress( );
```

## <a name="return-value"></a>傳回值

由 `BSTR` 包裝的 `_bstr_t` 指標。

## <a name="remarks"></a>備註

**GetAddress**會影響所有`_bstr_t`物件共用`BSTR`。 多個`_bstr_t`態度`BSTR`透過複製建構函式使用並**運算子 =**。

## <a name="example"></a>範例

請參閱[_bstr_t:: assign](../cpp/bstr-t-assign.md)範例使用**GetAddress**。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_bstr_t 類別](../cpp/bstr-t-class.md)
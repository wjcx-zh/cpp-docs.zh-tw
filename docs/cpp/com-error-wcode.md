---
title: _com_error::WCode
ms.date: 11/04/2016
f1_keywords:
- _com_error::WCode
helpviewer_keywords:
- WCode method [C++]
ms.assetid: f3b21852-f8ea-4e43-bff1-11c2d35454c4
ms.openlocfilehash: 92dffbdbe034ef55be04c1b7d204be6880d8d4b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190192"
---
# <a name="_com_errorwcode"></a>_com_error::WCode

**Microsoft 專屬**

抓取對應至封裝 HRESULT 的16位錯誤碼。

## <a name="syntax"></a>語法

```
WORD WCode ( ) const throw( );
```

## <a name="return-value"></a>傳回值

如果 HRESULT 在0x80040200 到0X8004ffff 內的範圍內，`WCode` 方法會傳回 HRESULT 減 0x80040200;否則，它會傳回零。

## <a name="remarks"></a>備註

`WCode` 方法是用來復原在 COM 支援程式碼中發生的對應。 `dispinterface` 屬性或方法的包裝函式，會呼叫封裝引數並呼叫 `IDispatch::Invoke`的支援常式。 傳回時，如果傳回 `DISP_E_EXCEPTION` 的失敗 HRESULT，則會從傳遞給 `IDispatch::Invoke`的 `EXCEPINFO` 結構中取出錯誤資訊。 錯誤碼可以是儲存在 `EXCEPINFO` 結構的 `wCode` 成員中的16位值，或 `EXCEPINFO` 結構之 `scode` 成員中的完整32位值。 如果傳回16位 `wCode`，則必須先將它對應到32位的失敗 HRESULT。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_error::HRESULTToWCode](../cpp/com-error-hresulttowcode.md)<br/>
[_com_error::WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)<br/>
[_com_error 類別](../cpp/com-error-class.md)

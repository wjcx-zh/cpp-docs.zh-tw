---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170797"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 專屬**

指定 `CLSID` 或 `ProgID`，附加至物件的現有實例。

## <a name="syntax"></a>語法

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>參數

*rclsid*<br/>
物件的 `CLSID`。

*clsidString*<br/>
保存 `CLSID` （以 " **{** " 為開頭）或 `ProgID`的 Unicode 字串。

*clsidStringA*<br/>
使用 ANSI 字碼頁的多位元組字元串，其中包含 `CLSID` （以 " **{** " 為開頭）或 `ProgID`。

## <a name="remarks"></a>備註

這些成員函式會呼叫**GetActiveObject** ，以取得已向 OLE 註冊之執行中物件的指標，然後查詢此智慧型指標的介面類別型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 呼叫 `Release` 以遞減先前封裝之指標的參考計數。 此常式會傳回 HRESULT 以表示成功或失敗。

- **GetActiveObject （** `rclsid` **）** 指定 `CLSID`，附加至物件的現有實例。

- **GetActiveObject （** `clsidString` **）** 附加至物件的現有實例，並指定保留 `CLSID` （以 " **{** " 為開頭）或 `ProgID`的 Unicode 字串。

- **GetActiveObject （** `clsidStringA` **）** 附加至物件的現有實例，並指定包含 `CLSID` （以 " **{** " 為開頭）或 `ProgID`的多位元組字元字串。 呼叫[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)

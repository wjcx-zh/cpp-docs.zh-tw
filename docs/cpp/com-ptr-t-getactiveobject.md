---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498886"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 專屬**

使用指定的`CLSID`或`ProgID`, 附加至物件的現有實例。

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
物件`CLSID`的。

*clsidString*<br/>
保存`CLSID` (開頭為 " **{** ") 或的`ProgID`Unicode 字串。

*clsidStringA*<br/>
使用 ANSI 字碼頁的多位元組字元串, 其中包含`CLSID` (以 " **{** `ProgID`" 為開頭) 或。

## <a name="remarks"></a>備註

這些成員函式會呼叫**GetActiveObject** , 以取得已向 OLE 註冊之執行中物件的指標, 然後查詢此智慧型指標的介面類別型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 `Release`呼叫以遞減先前封裝之指標的參考計數。 此常式會傳回 HRESULT 以表示成功或失敗。

- **GetActiveObject (** `rclsid` **)** 會附加至指定`CLSID`之物件的現有實例。

- **GetActiveObject (** `clsidString` **)** 會附加至物件的現有實例, 指定的 Unicode `CLSID`字串會保留 ( `ProgID`開頭為 " **{** ") 或。

- **GetActiveObject (** `clsidStringA` **)** 會附加至物件的現有實例, 指定的多位元組字元`CLSID`字串會保留 ( `ProgID`開頭為 " **{** ") 或。 呼叫[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), 它會假設字串位於 ANSI 字碼頁, 而不是 OEM 字碼頁。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 2ec4e90c8f0c1009cc47e9022a09b3b8f7dbb284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189997"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft 專屬**

指定 `CLSID` 或 `ProgID`，建立物件的新實例。

## <a name="syntax"></a>語法

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>參數

*rclsid*<br/>
物件的 `CLSID`。

*clsidString*<br/>
保存 `CLSID` （以 " **{** " 為開頭）或 `ProgID`的 Unicode 字串。

*clsidStringA*<br/>
使用 ANSI 字碼頁的多位元組字元串，其中包含 `CLSID` （以 " **{** " 為開頭）或 `ProgID`。

*dwClsCoNtext*<br/>
執行中的可執行程式碼內容。

*pOuter*<br/>
[匯總](../atl/aggregation.md)的外部未知。

## <a name="remarks"></a>備註

這些成員函式會呼叫 `CoCreateInstance` 建立新的 COM 物件，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 呼叫 `Release` 以遞減先前封裝之指標的參考計數。 此常式會傳回 HRESULT 以表示成功或失敗。

- **CreateInstance （**  *rclsid* **，**  *dwClsCoNtext*  **）** 指定 `CLSID`，建立物件的新執行中實例。

- **CreateInstance （**  *clsidString* **，**  *dwClsCoNtext*  **）** 指定保留 `CLSID` （以 " **{** " 為開頭）或 `ProgID`的 Unicode 字串，建立物件的新執行中實例。

- **CreateInstance （**  *clsidStringA* **，**  *dwClsCoNtext*  **）** 指定保存 `CLSID` （開頭為 " **{** "）或 `ProgID`的多位元組字元字串，建立物件的新執行中實例。 呼叫[MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。

**END Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)

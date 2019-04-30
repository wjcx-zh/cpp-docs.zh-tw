---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: c4f6cd54b90ab5fab69f91df67a8bf60b0b658f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399354"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance

**Microsoft 專屬**

建立指定物件的新執行個體`CLSID`或`ProgID`。

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
`CLSID`的物件。

*clsidString*<br/>
Unicode 字串保存`CLSID`(開頭為"**{**") 或`ProgID`。

*clsidStringA*<br/>
多位元組的字串，並使用保留的 ANSI 字碼頁`CLSID`(開頭為"**{**") 或`ProgID`。

*dwClsContext*<br/>
執行中的可執行程式碼內容。

*pOuter*<br/>
外部未知[彙總](../atl/aggregation.md)。

## <a name="remarks"></a>備註

這些成員函式會呼叫 `CoCreateInstance` 建立新的 COM 物件，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 `Release` 呼叫以遞減先前封裝之指標的參考計數。 此常式會傳回指出成功或失敗的 HRESULT。

- **CreateInstance (***rclsid* **，***dwClsContext***)** 會建立新的執行個體，指定的物件`CLSID`.

- **CreateInstance (***clsidString* **，***dwClsContext***)** 建立指定之物件的新執行個體Unicode 字串，其中保存`CLSID`(開頭為"**{**") 或`ProgID`。

- **CreateInstance (***clsidStringA* **，***dwClsContext***)** 建立指定之物件的新執行個體保留的多位元組字元字串`CLSID`(開頭為"**{**") 或`ProgID`。 呼叫[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: 84e43de9c40baa3c596c68ed7739471c059cbac7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484496"
---
# <a name="comptrtgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Microsoft 專屬**

將附加至現有的執行個體的物件的給定`CLSID`或`ProgID`。

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
`CLSID`的物件。

*clsidString*<br/>
Unicode 字串保存`CLSID`(開頭為"**{**") 或`ProgID`。

*clsidStringA*<br/>
多位元組的字串，並使用保留的 ANSI 字碼頁`CLSID`(開頭為"**{**") 或`ProgID`。

## <a name="remarks"></a>備註

這些成員函式呼叫**GetActiveObject**擷取已向 OLE 執行物件的指標，然後查詢這個智慧型指標的介面類型。 然後產生的指標就會封裝在這個 `_com_ptr_t` 物件內。 `Release` 呼叫以遞減先前封裝之指標的參考計數。 此常式會傳回指出成功或失敗的 HRESULT。

- **GetActiveObject (**`rclsid`**)** 附加至現有的執行個體的指定物件`CLSID`。

- **GetActiveObject (**`clsidString`**)** 附加至現有的執行個體的物件指定的 Unicode 字串保存`CLSID`(開頭為"**{**") 或`ProgID`.

- **GetActiveObject (**`clsidStringA`**)** 附加至現有的執行個體的物件，指定保留的多位元組字元字串`CLSID`(開頭為"**{**") 或`ProgID`. 呼叫[MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar)，它會假設字串位於 ANSI 字碼頁，而不是 OEM 字碼頁。

**結束 Microsoft 專屬**

## <a name="see-also"></a>另請參閱

[_com_ptr_t 類別](../cpp/com-ptr-t-class.md)
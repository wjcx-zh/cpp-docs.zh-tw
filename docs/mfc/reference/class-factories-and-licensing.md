---
title: Class Factory 和授權
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: e3fed6520cdbe0fd964e4e80e7c9ed9b78296d16
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372302"
---
# <a name="class-factories-and-licensing"></a>Class Factory 和授權

若要建立 OLE 控制項的執行個體，容器應用程式會呼叫控制項之 Class Factory 的成員函式。 由於您的控制項是一個實際的 OLE 物件，Class Factory 會負責為您的控制項建立執行個體。 每個 OLE 控制項類別必須有一個 Class Factory。

OLE 控制項的另一個重要功能是其強制執行授權的能力。 ControlWizard 可讓您在專案建立控制項期間合併授權。 有關控制項授權的詳細資訊,請參閱[ActiveX 控制件:授權 ActiveX 控制件](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

下表列出用於幾個用於宣告和實作控制項的 Class Factory，以及控制項授權的巨集和函式。

### <a name="class-factories-and-licensing"></a>Class Factory 和授權

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|宣告 OLE 控制項或屬性頁面的 Class Factory。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|實作控制項的 `GetClassID` 函式並宣告 Class Factory 的執行個體。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|所有授權函式宣告的開頭。|
|[END_OLEFACTORY](#end_olefactory)|所有授權函式宣告的結尾。|
|[AfxVerifyLicFile](#afxverifylicfile)|驗證控制項是否獲得在特定電腦上使用的授權。|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

聲明類工廠和控制類`GetClassID`的成員函數。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
控件類的名稱。

### <a name="remarks"></a>備註

對於不支援許可的控制項,在控制項類標頭檔中使用此宏。

請注意,此宏的作用與以下代碼範例相同:

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

實現控制項的類工廠和控制類的[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)成員函數。

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制件屬性頁類的名稱。

*external_name*<br/>
公開給應用程式的物件名稱。

*l, w1, w2, b1, b2, b3, b4, b5, b6, b7, b8*<br/>
類 CLSID 的元件。 有關這些參數的詳細資訊,請參閱[IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)的備註。

### <a name="remarks"></a>備註

對於使用DECLARE_OLECREATE_EX宏或BEGIN_OLEFACTORY和END_OLEFACTORY宏的任何控件類,此宏必須出現在實現檔中。 外部名稱是受其他應用程式公開的 OLE 控制項的標識碼。 容器使用此名稱請求此控制項類的物件。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a>BEGIN_OLEFACTORY

在控件類的標頭檔中開始類工廠的聲明。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
指定類出廠的控件類的名稱。

### <a name="remarks"></a>備註

類工廠許可功能的聲明應在BEGIN_OLEFACTORY後立即開始。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="end_olefactory"></a><a name="end_olefactory"></a>END_OLEFACTORY

結束控件的類工廠的聲明。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
類工廠是控件類的名稱。

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a>Afx 驗證檔案

呼叫此函數以驗證所`pszLicFileName`命名的許可證檔是否對 OLE 控制項有效。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
與許可控制項關聯的 DLL 的實體句柄。

*psslic 檔案名稱*<br/>
包含授權檔案名的 null 中止字串。

*psslic 檔案內容*<br/>
指向必須匹配許可證檔開頭找到的序列的位元組序列。

*cch*<br/>
*pszlicFile內容中的*字元數。

### <a name="return-value"></a>傳回值

如果許可證檔存在,並且以*pszLicFile 內容*中的字元序列開頭,則非零;否則 0。

### <a name="remarks"></a>備註

如果*cch*為 -1,則此功能使用:

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>需求

  **頭**afxctl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

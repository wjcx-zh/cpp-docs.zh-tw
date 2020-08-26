---
title: Class Factory 和授權
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 939d7156a9bd7bf0778d2ab4a40acb2afe10cf6e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845922"
---
# <a name="class-factories-and-licensing"></a>Class Factory 和授權

若要建立 OLE 控制項的執行個體，容器應用程式會呼叫控制項之 Class Factory 的成員函式。 由於您的控制項是一個實際的 OLE 物件，Class Factory 會負責為您的控制項建立執行個體。 每個 OLE 控制項類別必須有一個 Class Factory。

OLE 控制項的另一個重要功能是其強制執行授權的能力。 ControlWizard 可讓您在專案建立控制項期間合併授權。 如需控制授權的詳細資訊，請參閱 [activex 控制項：授權 Activex 控制項一](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)文。

下表列出用於幾個用於宣告和實作控制項的 Class Factory，以及控制項授權的巨集和函式。

### <a name="class-factories-and-licensing"></a>Class Factory 和授權

|宏或函式|描述|
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|宣告 OLE 控制項或屬性頁面的 Class Factory。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|實作控制項的 `GetClassID` 函式並宣告 Class Factory 的執行個體。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|所有授權函式宣告的開頭。|
|[END_OLEFACTORY](#end_olefactory)|所有授權函式宣告的結尾。|
|[AfxVerifyLicFile](#afxverifylicfile)|驗證控制項是否獲得在特定電腦上使用的授權。|

## <a name="declare_olecreate_ex"></a><a name="declare_olecreate_ex"></a> DECLARE_OLECREATE_EX

宣告 class factory 和 `GetClassID` control 類別的成員函式。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制項類別的名稱。

### <a name="remarks"></a>備註

針對不支援授權的控制項，在控制項類別標頭檔中使用此宏。

請注意，這個宏的用途與下列程式碼範例相同：

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="implement_olecreate_ex"></a><a name="implement_olecreate_ex"></a> IMPLEMENT_OLECREATE_EX

實控制項的 class factory 和控制項類別的 [GetClassID](../../mfc/reference/colecontrol-class.md#getclassid) 成員函式。

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
控制項屬性頁類別的名稱。

*external_name*<br/>
公開給應用程式的物件名稱。

*l、w1、w2、b1、b2、b3、b4、b5、b6、b7、b8*<br/>
類別 CLSID 的元件。 如需這些參數的詳細資訊，請參閱 [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)的備註。

### <a name="remarks"></a>備註

此宏必須出現在使用 DECLARE_OLECREATE_EX 宏或 BEGIN_OLEFACTORY 和 END_OLEFACTORY 宏之任何控制項類別的執行檔中。 外部名稱是對其他應用程式公開之 OLE 控制項的識別碼。 容器會使用這個名稱來要求這個控制項類別的物件。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="begin_olefactory"></a><a name="begin_olefactory"></a> BEGIN_OLEFACTORY

開始在控制項類別的標頭檔中宣告 class factory。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
指定類別 factory 為其類別的控制項類別名稱。

### <a name="remarks"></a>備註

Class factory 授權函式的宣告應該會在 BEGIN_OLEFACTORY 之後立即開始。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="end_olefactory"></a><a name="end_olefactory"></a> END_OLEFACTORY

結束控制項之 class factory 的宣告。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
Class factory 為其類別的控制項類別名稱。

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="afxverifylicfile"></a><a name="afxverifylicfile"></a> AfxVerifyLicFile

呼叫此函式，以確認名為的授權檔案 `pszLicFileName` 對 OLE 控制項而言是有效的。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
與授權控制項相關聯之 DLL 的實例控制碼。

*pszLicFileName*<br/>
指向以 null 終止的字元字串，其中包含授權檔案名。

*pszLicFileContents*<br/>
指向必須符合在授權檔案開頭找到之順序的位元組序列。

*cch*<br/>
*PszLicFileContents*中的字元數。

### <a name="return-value"></a>傳回值

如果授權檔案存在且開頭為 *pszLicFileContents*中的字元序列，則為非零。否則為0。

### <a name="remarks"></a>備註

如果 *cch* 為-1，此函式會使用：

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>規格需求

  **標頭** afxctl.h。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

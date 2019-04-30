---
title: Class Factory 和授權
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.classes
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 3788d904bf903481d57dd73a28bf6eafadd5f019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392553"
---
# <a name="class-factories-and-licensing"></a>Class Factory 和授權

若要建立 OLE 控制項的執行個體，容器應用程式會呼叫控制項之 Class Factory 的成員函式。 由於您的控制項是一個實際的 OLE 物件，Class Factory 會負責為您的控制項建立執行個體。 每個 OLE 控制項類別必須有一個 Class Factory。

OLE 控制項的另一個重要功能是其強制執行授權的能力。 ControlWizard 可讓您在專案建立控制項期間合併授權。 如需控制項授權的詳細資訊，請參閱文章[ActiveX 控制項：授權 ActiveX 控制項](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)。

下表列出用於幾個用於宣告和實作控制項的 Class Factory，以及控制項授權的巨集和函式。

### <a name="class-factories-and-licensing"></a>Class Factory 和授權

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|宣告 OLE 控制項或屬性頁面的 Class Factory。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|實作控制項的 `GetClassID` 函式並宣告 Class Factory 的執行個體。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|所有授權函式宣告的開頭。|
|[END_OLEFACTORY](#end_olefactory)|所有授權函式宣告的結尾。|
|[AfxVerifyLicFile](#afxverifylicfile)|驗證控制項是否獲得在特定電腦上使用的授權。|

##  <a name="declare_olecreate_ex"></a>  DECLARE_OLECREATE_EX

宣告 class factory 和`GetClassID`控制類別成員函式。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
控制項類別的名稱。

### <a name="remarks"></a>備註

使用這個巨集不支援授權的控制項的控制項類別標頭檔中。

請注意，這個巨集有相同的用途，下列程式碼範例為：

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="implement_olecreate_ex"></a>  IMPLEMENT_OLECREATE_EX

實作控制項的 class factory 和[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)控制類別成員函式。

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
對應用程式公開物件名稱。

*l、 w1、 w2、 b1，b2，b3、 b4、 b5、 b6、 b7、 b8*<br/>
元件類別的 CLSID。 如需有關這些參數的詳細資訊，請參閱的 < 備註 > [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)。

### <a name="remarks"></a>備註

這個巨集必須出現在任何使用 DECLARE_OLECREATE_EX 巨集或 BEGIN_OLEFACTORY 和 END_OLEFACTORY 巨集的控制項類別的實作檔案中。 External name 是公開給其他應用程式的 OLE 控制項的識別項。 容器會使用此名稱來要求這個控制項類別的物件。

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="begin_olefactory"></a>  BEGIN_OLEFACTORY

開始您的類別處理站，您的控制項類別的標頭檔中的宣告。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
指定控制項類別這是其類別處理站的名稱。

### <a name="remarks"></a>備註

授權函式的類別處理站的宣告應 BEGIN_OLEFACTORY 之後立即開始。

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="end_olefactory"></a>  END_OLEFACTORY

結束控制項的 class factory 的宣告。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>參數

*class_name*<br/>
這是其類別 factory 類別的控制項名稱。

### <a name="requirements"></a>需求

  **標頭**afxctl.h

##  <a name="afxverifylicfile"></a>  AfxVerifyLicFile

呼叫此函式，以確認授權檔案是由命名`pszLicFileName`適用於 OLE 控制項。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>參數

*hInstance*<br/>
授權的控制項相關聯的 dll 執行個體控制代碼。

*pszLicFileName*<br/>
指向以 null 結束的字元字串，包含授權檔名。

*pszLicFileContents*<br/>
必須符合授權檔案的開頭，請參閱序列的位元組序列的點。

*cch*<br/>
中的字元數*pszLicFileContents*。

### <a name="return-value"></a>傳回值

如果授權檔案存在，而且中的字元序列的開頭為非零*pszLicFileContents*，否則為 0。

### <a name="remarks"></a>備註

如果*cch*為-1，此函式會使用：

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>需求

  **標頭**afxctl.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)

---
title: CMFCPropertyGridFileProperty 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 4b64d18a67ea499c202b81481684227200846483
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821277"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty 類別

`CMFCPropertyGridFileProperty`類別支援可開啟 [檔案選取] 對話方塊的屬性清單控制項專案。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|建構 `CMFCPropertyGridFileProperty` 物件。|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|供架構用來取得與這個類別類型相關聯之[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyGridFileProperty::OnClickButton`|(覆寫[CMFCPropertyGridProperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

### <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>需求

**標頭:** afxpropertygridctrl。h

##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty:: CMFCPropertyGridFileProperty

建構 `CMFCPropertyGridFileProperty` 物件。

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>參數

*strName*<br/>
在屬性名稱。

*bOpenFileDialog*<br/>
在TRUE 表示開啟 [**開啟**檔案] 對話方塊;FALSE 表示開啟 [**儲存**盤案] 對話方塊。

*strFileName*<br/>
在初始檔案名。

*lpszDefExt*<br/>
在一或多個副檔名的字串。 預設值為 Null。

*dwFlags*<br/>
在對話方塊旗標。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。

*lpszFilter*<br/>
在一或多個檔案篩選準則的字串。 預設值為 Null。

*lpszDescr*<br/>
在屬性專案描述。 預設值為 Null。

*dwData*<br/>
在與屬性專案相關聯的應用程式特定資料。 例如，32 位元整數或其他資料的指標。 預設值為 0。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

如需可用旗標的完整清單, 請參閱[OPENFILENAME 結構](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

### <a name="example"></a>範例

下列範例示範如何使用 `CMFCPropertyGridFileProperty` 類別的建構函式來建立物件 。 這個範例是[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)

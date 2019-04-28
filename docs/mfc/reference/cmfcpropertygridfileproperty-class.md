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
ms.openlocfilehash: 20a0a50198357602d70a2111c6884058f7578af7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326695"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty 類別

`CMFCPropertyGridFileProperty`類別支援開啟檔案選取對話方塊的屬性清單控制項項目。

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
|`CMFCPropertyGridFileProperty::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|
|`CMFCPropertyGridFileProperty::OnClickButton`|(覆寫[cmfcpropertygridproperty:: Onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)。)|

### <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>需求

**標頭：** afxpropertygridctrl.h

##  <a name="cmfcpropertygridfileproperty"></a>  CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty

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
[in]屬性名稱。

*bOpenFileDialog*<br/>
[in]True 會開放**開啟檔案**此對話方塊。若要開啟，則為 FALSE**儲存檔案** 對話方塊。

*strFileName*<br/>
[in]初始檔案名稱。

*lpszDefExt*<br/>
[in]一或多個檔案名稱副檔名的字串。 預設值是 NULL。

*dwFlags*<br/>
[in]對話方塊旗標。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。

*lpszFilter*<br/>
[in]一或多個檔案篩選器的字串。 預設值是 NULL。

*lpszDescr*<br/>
[in]屬性項目描述。 預設值是 NULL。

*dwData*<br/>
[in]屬性項目相關聯的應用程式專屬資料。 例如，32 位元整數或其他資料的指標。 預設值為 0。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

可用的旗標完整清單，請參閱 < [OPENFILENAME 結構](/windows/desktop/api/commdlg/ns-commdlg-tagofna)。

### <a name="example"></a>範例

下列範例示範如何使用 `CMFCPropertyGridFileProperty` 類別的建構函式來建立物件 。 此範例中是屬於[Visual Studio 示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)

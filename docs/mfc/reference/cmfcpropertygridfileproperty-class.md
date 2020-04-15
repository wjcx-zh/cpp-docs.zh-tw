---
title: CMFC財產網格檔案屬性類別
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 0ce3321968f0c29ce3b946f6127e4435b531c422
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81360574"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFC財產網格檔案屬性類別

類`CMFCPropertyGridFileProperty`支援打開檔案選擇對話方塊的屬性清單控制項。

## <a name="syntax"></a>語法

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CMFC 屬性網格檔案屬性:CMFC財產網格檔案屬性](#cmfcpropertygridfileproperty)|建構 `CMFCPropertyGridFileProperty` 物件。|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|解構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|框架用於獲取指向與此類類型關聯的[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)物件的指標。|
|`CMFCPropertyGridFileProperty::OnClickButton`|(覆寫[CMFC 屬性網格屬性::按一下按鈕](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton).)|

### <a name="remarks"></a>備註

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>需求

**標題:** afxpropertygridctrl.h

## <a name="cmfcpropertygridfilepropertycmfcpropertygridfileproperty"></a><a name="cmfcpropertygridfileproperty"></a>CMFC 屬性網格檔案屬性:CMFC財產網格檔案屬性

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
[在]屬性名稱。

*b 開啟檔案對話*<br/>
[在]TRUE 打開**打開檔案**對話方塊;FALSE 以打開 **「儲存檔案」** 對話框。

*strFilename*<br/>
[在]初始檔名。

*lpszDefExt*<br/>
[在]一個或多個檔案名副檔名的字串。 預設值是 NULL。

*dwFlags*<br/>
[在]對話框標誌。 預設值是 OFN_HIDEREADONLY 和 OFN_OVERWRITEPROMPT 的位元組合 (OR)。

*lpszFilter*<br/>
[在]一個或多個檔案篩選器的字串。 預設值是 NULL。

*lpszDescr*<br/>
[在]屬性項描述。 預設值是 NULL。

*dwData*<br/>
[在]與屬性項關聯的特定於應用程式的數據。 例如，32 位元整數或其他資料的指標。 預設值為 0。

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

關於可用的旗標的清單,請參閱[OPENFILENAME 結構](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)。

### <a name="example"></a>範例

下列範例示範如何使用 `CMFCPropertyGridFileProperty` 類別的建構函式來建立物件 。 此示例是[可視化工作室演示範例](../../overview/visual-cpp-samples.md)的一部分。

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)

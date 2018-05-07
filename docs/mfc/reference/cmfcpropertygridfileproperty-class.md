---
title: CMFCPropertyGridFileProperty 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
dev_langs:
- C++
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2b123b5c473c834e958263edb926ef25103d788
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|`CMFCPropertyGridFileProperty::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
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
 [輸入] `strName`  
 屬性名稱。  
  
 [輸入] `bOpenFileDialog`  
 `TRUE` 若要開啟**開啟檔案** 對話方塊。`FALSE`開啟**儲存檔案** 對話方塊。  
  
 [輸入] `strFileName`  
 初始檔案名稱。  
  
 [輸入] `lpszDefExt`  
 一或多個副檔名的字串。 預設值是 `NULL`。  
  
 [輸入] `dwFlags`  
 對話方塊旗標。 預設值是 `OFN_HIDEREADONLY` 和 `OFN_OVERWRITEPROMPT` 的位元組合 (OR)。  
  
 [輸入] `lpszFilter`  
 一或多個檔案篩選條件的字串。 預設值是 `NULL`。  
  
 [輸入] `lpszDescr`  
 屬性項目說明。 預設值是 `NULL`。  
  
 [輸入] `dwData`  
 屬性項目相關聯的應用程式專屬資料。 例如，32 位元整數或其他資料的指標。 預設值為 0。  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
 如需可用旗標的完整清單，請參閱[OPENFILENAME 結構](https://msdn.microsoft.com/library/ms646839.aspx)。  
  
### <a name="example"></a>範例  
 下列範例示範如何使用 `CMFCPropertyGridFileProperty` 類別的建構函式來建立物件 。 這個範例是屬於[Visual Studio 示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCPropertyGridCtrl 類別](../../mfc/reference/cmfcpropertygridctrl-class.md)   
 [CMFCPropertyGridProperty 類別](../../mfc/reference/cmfcpropertygridproperty-class.md)

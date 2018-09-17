---
title: CMFCCustomColorsPropertyPage 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage
- AFXCUSTOMCOLORSPROPERTYPAGE/CMFCCustomColorsPropertyPage::Setup
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage [MFC], Setup
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c8fea125c61bebe836a31c0b2718741e8c531d3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716847"
---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 類別
表示屬性頁，可以在 [色彩] 對話方塊中選取自訂色彩。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCCustomColorsPropertyPage::CMFCCustomColorsPropertyPage`|預設建構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|`CMFCCustomColorsPropertyPage::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCCustomColorsPropertyPage::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|設定色彩元件的屬性頁。|  
  
### <a name="remarks"></a>備註  
 `CMFCColorDialog`類別會使用這個類別來顯示 [自訂色彩] 屬性頁。 如需詳細資訊`CMFCColorDialog`，請參閱 < [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCCustomColorsPropertyPage`物件，並設定 [屬性] 頁面的色彩元件。  
  
 [!code-cpp[NVC_MFC_RibbonApp#35](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcustomcolorspropertypage.h  
  
##  <a name="setup"></a>  CMFCCustomColorsPropertyPage::Setup  
 設定色彩元件的屬性頁。  
  
```  
void Setup(
    BYTE R,  
    BYTE G,  
    BYTE B);
```  
  
### <a name="parameters"></a>參數  
  
|||  
|-|-|  
|參數|描述|  
|*R*|[in]紅色的 RGB 值的元件。|  
|*G*|[in]綠色的 RGB 值的元件。|  
|*B*|[in]RGB 值的藍色元件。|  
  
### <a name="remarks"></a>備註  
 這個方法會更新目前的 RGB 和關聯的 HLS （色調、 亮度和飽和度） 色彩值的屬性頁。 [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)架構初始化 [色彩] 對話方塊中，或使用者按下滑鼠左的按鈕時，方法會呼叫這個方法。 如需詳細資訊`CMFCColorDialog`，請參閱 < [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage 類別](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)

---
title: "CMFCCustomColorsPropertyPage 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCCustomColorsPropertyPage
dev_langs:
- C++
helpviewer_keywords:
- CMFCCustomColorsPropertyPage class
ms.assetid: 46a45ba2-1fda-440d-8018-d4dcd44f5816
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: fa534f22438b7be37e7893e545c3e060df69384f
ms.lasthandoff: 02/24/2017

---
# <a name="cmfccustomcolorspropertypage-class"></a>CMFCCustomColorsPropertyPage 類別
代表可以在色彩對話方塊中選取自訂色彩的屬性頁。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCCustomColorsPropertyPage : public CPropertyPage  
```  
  
## <a name="members"></a>Members  
  
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
|`CMFCCustomColorsPropertyPage::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCCustomColorsPropertyPage::Setup](#setup)|設定 [屬性] 頁面上的色彩元件。|  
  
### <a name="remarks"></a>備註  
 `CMFCColorDialog`類別會使用這個類別來顯示 [自訂色彩] 屬性頁。 如需詳細資訊`CMFCColorDialog`，請參閱[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCCustomColorsPropertyPage`物件，並設定 [屬性] 頁面上的色彩元件。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&35;](../../mfc/reference/codesnippet/cpp/cmfccustomcolorspropertypage-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 [CPropertyPage](../../mfc/reference/cpropertypage-class.md)  
  
 [CMFCCustomColorsPropertyPage](../../mfc/reference/cmfccustomcolorspropertypage-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxcustomcolorspropertypage.h  
  
##  <a name="a-namesetupa--cmfccustomcolorspropertypagesetup"></a><a name="setup"></a>CMFCCustomColorsPropertyPage::Setup  
 設定 [屬性] 頁面上的色彩元件。  
  
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
|[in] `R`|紅元件的 RGB 值。|  
|[in] `G`|綠元件的 RGB 值。|  
|[in] `B`|藍元件的 RGB 值。|  
  
### <a name="remarks"></a>備註  
 這個方法會更新目前的 RGB 和相關聯的 HLS （色調、 亮度及飽和度） 色彩值的屬性頁。 [CMFCColorDialog::SetPageTwo](../../mfc/reference/cmfccolordialog-class.md#setpagetwo)架構初始化色彩 對話方塊，或使用者按下滑鼠左鍵時，方法會呼叫這個方法。 如需詳細資訊`CMFCColorDialog`，請參閱[CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCColorDialog 類別](../../mfc/reference/cmfccolordialog-class.md)   
 [CMFCStandardColorsPropertyPage 類別](../../mfc/reference/cmfcstandardcolorspropertypage-class.md)


---
title: CMFCRibbonApplicationButton 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonApplicationButton [MFC], CMFCRibbonApplicationButton
- CMFCRibbonApplicationButton [MFC], SetImage
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17efa63488a736089c988e6cfbb7bd97330816aa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701385"
---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton 類別
實作位於應用程式視窗左上角的特殊按鈕。 按一下按鈕時，按鈕會開啟通常包含一般 [ **檔案** ] 命令 (例如 [ **開啟**]、[ **儲存**] 和 [ **結束**]) 的功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|建構並初始化 `CMFCRibbonApplicationButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|`CMFCRibbonApplicationButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonApplicationButton::GetThisClass`|Framework 用來取得的指標[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|將映像指派給功能區應用程式按鈕。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用中的各種方法`CMFCRibbonApplicationButton`類別。 此範例示範如何將影像指派給應用程式 按鈕，以及如何設定其工具提示。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DrawClient#4](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient#5](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭：** afxRibbonBar.h  
  
##  <a name="cmfcribbonapplicationbutton"></a>  CMFCRibbonApplicationButton::CMFCRibbonApplicationButton  
 建構並初始化[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)物件。  
  
```  
CMFCRibbonApplicationButton();  
CMFCRibbonApplicationButton(UINT uiBmpResID);  
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>參數  
 *uiBmpResID*  
 在 [應用程式] 按鈕上顯示影像的資源識別碼。  
  
 *hBmp*  
 在 [應用程式] 按鈕上顯示點陣圖控制代碼。  
  
### <a name="remarks"></a>備註  
 功能區應用程式按鈕是位於應用程式視窗左上角的特殊按鈕。 當使用者按一下此按鈕時，應用程式，將會開啟通常包含一般的功能表**檔案**命令，例如**開放**，**儲存**，和**結束**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 將映像指派給應用程式按鈕。  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>參數  
*uiBmpResID*<br/>
[in]在 [應用程式] 按鈕上顯示影像的資源識別碼。  
  
*hBmp*<br/>
[in]在 [應用程式] 按鈕上顯示點陣圖控制代碼。  
  
### <a name="remarks"></a>備註  
 若要將新的映像指派給功能區應用程式按鈕，在您建立按鈕之後，使用這個方法。 應用程式視窗左上角，位於 [應用程式] 按鈕。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)

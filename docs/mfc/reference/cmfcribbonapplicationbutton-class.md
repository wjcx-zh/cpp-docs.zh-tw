---
title: CMFCRibbonApplicationButton 類別 |Microsoft 文件
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
ms.openlocfilehash: 3b2b2e8adccd77862b445d7e91df0b808967a31d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|`CMFCRibbonApplicationButton::GetThisClass`|由架構用來取得指向[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與此類別類型相關聯的物件。|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|將映像指派給功能區應用程式按鈕。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonApplicationButton`類別。 此範例顯示如何將映像指派給應用程式 按鈕，以及如何設定其工具提示。 這段程式碼片段是 [Draw 用戶端範例](../../visual-cpp-samples.md)的一部分。  
  
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
 `uiBmpResID`  
 在應用程式按鈕上顯示的影像資源識別碼。  
  
 `hBmp`  
 在應用程式按鈕上顯示點陣圖的控制代碼。  
  
### <a name="remarks"></a>備註  
 功能區應用程式按鈕是位於應用程式視窗左上角的特殊按鈕。 當使用者按一下此按鈕時，應用程式會開啟通常包含一般功能表**檔案**命令，例如**開啟**，**儲存**，和**結束**.  
  
##  <a name="setimage"></a>  CMFCRibbonApplicationButton::SetImage  
 將映像指派給應用程式按鈕。  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `uiBmpResID`  
 在應用程式按鈕上顯示的影像資源識別碼。  
  
 [輸入] `hBmp`  
 在應用程式按鈕上顯示點陣圖的控制代碼。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法後建立按鈕的功能區應用程式按鈕指派新的映像。 應用程式按鈕位於應用程式視窗左上角。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)

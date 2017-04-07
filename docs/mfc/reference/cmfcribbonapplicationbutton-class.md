---
title: "CMFCRibbonApplicationButton 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::CMFCRibbonApplicationButton
- AFXRIBBONBAR/CMFCRibbonApplicationButton::SetImage
dev_langs:
- C++
helpviewer_keywords:
- CMFCRibbonApplicationButton class
ms.assetid: beb81757-fabd-4641-9130-876ba8505b78
caps.latest.revision: 25
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: a6fc19c2af854f3cd4ee3dc3a3008abcb4714ba3
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcribbonapplicationbutton-class"></a>CMFCRibbonApplicationButton 類別
實作位於應用程式視窗左上角的特殊按鈕。 按一下按鈕時，按鈕會開啟通常包含一般 [ **檔案** ] 命令 (例如 [ **開啟**]、[ **儲存**] 和 [ **結束**]) 的功能表。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCRibbonApplicationButton : public CMFCRibbonButton  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCRibbonApplicationButton::CMFCRibbonApplicationButton](#cmfcribbonapplicationbutton)|建構並初始化 `CMFCRibbonApplicationButton` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCRibbonApplicationButton::CreateObject`|由建立此類別類型的動態執行個體架構所使用。|  
|`CMFCRibbonApplicationButton::GetThisClass`|由架構用來取得變數的指標， [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)與這個類別的型別相關聯的物件。|  
|[CMFCRibbonApplicationButton::SetImage](#setimage)|將影像指派給功能區應用程式 按鈕。|  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種方法的`CMFCRibbonApplicationButton`類別。 此範例顯示如何將影像指派給應用程式 按鈕，以及如何設定其工具提示。 此程式碼片段是一部分[繪製的用戶端範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DrawClient #&4;](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_1.h)]  
[!code-cpp[NVC_MFC_DrawClient #&5;](../../mfc/reference/codesnippet/cpp/cmfcribbonapplicationbutton-class_2.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)  
  
 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxRibbonBar.h  
  
##  <a name="cmfcribbonapplicationbutton"></a>CMFCRibbonApplicationButton::CMFCRibbonApplicationButton  
 建構並初始化[CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)物件。  
  
```  
CMFCRibbonApplicationButton();  
CMFCRibbonApplicationButton(UINT uiBmpResID);  
  CMFCRibbonApplicationButton(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>參數  
 `uiBmpResID`  
 在 [應用程式] 按鈕上顯示影像的資源識別碼。  
  
 `hBmp`  
 在應用程式按鈕上顯示的點陣圖控制代碼。  
  
### <a name="remarks"></a>備註  
 功能區應用程式按鈕是位於應用程式視窗左上角的特殊按鈕。 當使用者按一下此按鈕時，應用程式可開啟功能表通常包含一般**檔案**命令，例如**開啟**，**儲存**，和**結束**。  
  
##  <a name="setimage"></a>CMFCRibbonApplicationButton::SetImage  
 將影像指派給應用程式 按鈕。  
  
```  
void SetImage(UINT uiBmpResID);  
void SetImage(HBITMAP hBmp);
```  
  
### <a name="parameters"></a>參數  
 [in] `uiBmpResID`  
 在 [應用程式] 按鈕上顯示影像的資源識別碼。  
  
 [in] `hBmp`  
 在應用程式按鈕上顯示的點陣圖控制代碼。  
  
### <a name="remarks"></a>備註  
 您可以使用這個方法後建立按鈕的功能區應用程式按鈕指派新的映像。 應用程式按鈕位於應用程式視窗左上角。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonButton 類別](../../mfc/reference/cmfcribbonbutton-class.md)


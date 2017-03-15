---
title: "CMFCAcceleratorKey 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKey
dev_langs:
- C++
helpviewer_keywords:
- CMFCAcceleratorKey class
ms.assetid: d140fbf7-23db-45ea-a63e-414a5ec7b3d5
caps.latest.revision: 36
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
ms.openlocfilehash: 7baa210acfabe8f17e2ab747fd98fe463c2907a2
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcacceleratorkey-class"></a>CMFCAcceleratorKey 類別
實作虛擬按鍵對應和格式化的協助程式類別。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCAcceleratorKey : public CObject  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CMFCAcceleratorKey::CMFCAcceleratorKey](#cmfcacceleratorkey)|建構 `CMFCAcceleratorKey` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCAcceleratorKey::Format](#format)|將轉譯加速度結構，以視覺表示法。|  
|[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)|設定的快速鍵`CMFCAcceleratorKey`物件。|  
  
## <a name="remarks"></a>備註  
 快速鍵是也稱為捷徑按鍵。 如果您想要顯示的鍵盤快速鍵，則當使用者輸入， [CMFCAcceleratorKeyAssignCtrl 類別](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)對應鍵盤快速鍵，例如 Alt + Shift + S、 自訂文字格式，例如"Alt + Shift + S"。 每個`CMFCAcceleratorKey`物件將單一快速鍵對應至文字格式。  
  
 如需如何使用快速鍵和快速鍵對應表的詳細資訊，請參閱[CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構`CMFCAcceleratorKey`物件，以及如何使用其`Format`方法。  
  
 [!code-cpp[NVC_MFC_RibbonApp #&30;](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkey-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CMFCAcceleratorKey`   
  
## <a name="requirements"></a>需求  
 **標頭︰** afxacceleratorkey.h  
  
##  <a name="a-namecmfcacceleratorkeya--cmfcacceleratorkeycmfcacceleratorkey"></a><a name="cmfcacceleratorkey"></a>CMFCAcceleratorKey::CMFCAcceleratorKey  
 建構[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)物件。  
  
```  
CMFCAcceleratorKey();  
CMFCAcceleratorKey(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpAccel`  
 快速鍵指標。  
  
### <a name="remarks"></a>備註  
 當您建立時如果您未提供的快速鍵`CMFCAccleratorKey`，使用[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)方法產生關聯的快速鍵與您`CMFCAcceleratorKey`物件。  
  
##  <a name="a-nameformata--cmfcacceleratorkeyformat"></a><a name="format"></a>CMFCAcceleratorKey::Format  
 將轉譯加速度結構及其相關聯的字串值。  
  
```  
void Format(CString& str) const;  
```  
  
### <a name="parameters"></a>參數  
 [輸出] `str`  
 參考`CString`物件，方法會將轉譯的快速鍵。  
  
### <a name="remarks"></a>備註  
 這個方法會擷取字串的格式相關的快速鍵。 您可以設定的字串格式[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)物件建構函式或方法使用[CMFCAcceleratorKey::SetAccelerator](#setaccelerator)。  
  
##  <a name="a-namesetacceleratora--cmfcacceleratorkeysetaccelerator"></a><a name="setaccelerator"></a>CMFCAcceleratorKey::SetAccelerator  
 設定的快速鍵[CMFCAcceleratorKey](../../mfc/reference/cmfcacceleratorkey-class.md)物件。  
  
```  
void SetAccelerator(LPACCEL lpAccel);
```  
  
### <a name="parameters"></a>參數  
 [in] `lpAccel`  
 快速鍵指標。  
  
### <a name="remarks"></a>備註  
 使用此方法來設定的快速鍵`CMFCAcceleratorKey`您在建立時如果您未提供快顯金鑰`CMFCAcceleratorKey`。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CKeyboardManager 類別](../../mfc/reference/ckeyboardmanager-class.md)


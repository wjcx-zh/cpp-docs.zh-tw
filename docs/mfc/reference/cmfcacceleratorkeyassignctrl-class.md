---
title: "CMFCAcceleratorKeyAssignCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::GetAccel
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsFocused
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::IsKeyDefined
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage
- AFXACCELERATORKEYASSIGNCTRL/CMFCAcceleratorKeyAssignCtrl::ResetKey
dev_langs: C++
helpviewer_keywords:
- CMFCAcceleratorKeyAssignCtrl [MFC], CMFCAcceleratorKeyAssignCtrl
- CMFCAcceleratorKeyAssignCtrl [MFC], GetAccel
- CMFCAcceleratorKeyAssignCtrl [MFC], IsFocused
- CMFCAcceleratorKeyAssignCtrl [MFC], IsKeyDefined
- CMFCAcceleratorKeyAssignCtrl [MFC], PreTranslateMessage
- CMFCAcceleratorKeyAssignCtrl [MFC], ResetKey
ms.assetid: 89fb8e62-596e-4e71-8c9a-32740347aaab
caps.latest.revision: "33"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1aacd22af0b2e0e14a3c1203a42e067b1f339c71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cmfcacceleratorkeyassignctrl-class"></a>CMFCAcceleratorKeyAssignCtrl 類別
`CMFCAcceleratorKeyAssignCtrl`類別會擴充[CEdit 類別](../../mfc/reference/cedit-class.md)以支援額外的系統按鈕，例如 ALT、 CONTROL 和 SHIFT。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCAcceleratorKeyAssignCtrl : public CEdit  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl](#cmfcacceleratorkeyassignctrl)|建構 `CMFCAcceleratorKeyAssignCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)|針對在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下的快速鍵，擷取 `ACCEL` 結構。|  
|[CMFCAcceleratorKeyAssignCtrl::IsFocused](#isfocused)||  
|[CMFCAcceleratorKeyAssignCtrl::IsKeyDefined](#iskeydefined)|判斷是否已定義快速鍵。|  
|[CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage](#pretranslatemessage)|[CWinApp](../../mfc/reference/cwinapp-class.md) 類別用來轉譯分派至 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前的視窗訊息。 (覆寫 [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)。)|  
|[CMFCAcceleratorKeyAssignCtrl::ResetKey](#resetkey)|重設快速鍵。|  
  
## <a name="remarks"></a>備註  
 此類別可藉由支援快速鍵來擴充 `CEdit` 類別的功能。 `CMFCAcceleratorKeyAssignCtrl`類別函式做為[CEdit 類別](../../mfc/reference/cedit-class.md)，也可以辨認系統按鈕。  
  
 這個類別會將實體快速鍵組合對應至字串值。 例如，假設按鍵組合 ALT + B 會對應至字串 "Alt + B"。 當使用者在 `CMFCAcceleratorKeyAssignCtrl` 物件中按下此按鍵組合時，會對使用者顯示 "Alt + B"。 如需快捷鍵和字串格式之間的對應的詳細資訊，請參閱[CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何建構 `CMFCAcceleratorKeyAssignCtrl` 物件，並使用其 `ResetKey` 方法來重設快速鍵。  
  
 [!code-cpp[NVC_MFC_RibbonApp#31](../../mfc/reference/codesnippet/cpp/cmfcacceleratorkeyassignctrl-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CEdit](../../mfc/reference/cedit-class.md)  
  
 `CMFCAcceleratorKeyAssignCtrl`   
  
## <a name="requirements"></a>需求  
 **標頭：** afxacceleratorkeyassignctrl.h  
  
##  <a name="cmfcacceleratorkeyassignctrl"></a>CMFCAcceleratorKeyAssignCtrl::CMFCAcceleratorKeyAssignCtrl  
 建構[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。  
  
```  
CMFCAcceleratorKeyAssignCtrl();
```  
  
##  <a name="getaccel"></a>CMFCAcceleratorKeyAssignCtrl::GetAccel  
 擷取`ACCEL`結構中按下的快速鍵[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。  
  
```  
ACCEL const* GetAccel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 `ACCEL`結構描述的快速鍵。  
  
### <a name="remarks"></a>備註  
 使用這個函數來擷取`ACCEL`結構使用者輸入攠摝坫您`CMFCAcceleratorKeyAssignCtrl`物件。  
  
##  <a name="isfocused"></a>CMFCAcceleratorKeyAssignCtrl::IsFocused  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
BOOL IsFocused() const;  
```  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="iskeydefined"></a>CMFCAcceleratorKeyAssignCtrl::IsKeyDefined  
 判斷是否已在定義攠摝坫[CMFCAcceleratorKeyAssignCtrl](../../mfc/reference/cmfcacceleratorkeyassignctrl-class.md)物件。  
  
```  
BOOL IsKeyDefined() const;  
```  
  
### <a name="return-value"></a>傳回值  
 為非零，如果使用者已按下定義的快速鍵; 的索引鍵的有效組合否則便是 0。  
  
### <a name="remarks"></a>備註  
 使用此函數來判斷使用者是否輸入有效的快速鍵在您`CMFCAcceleratorKeyAssignCtrl`物件。 如果攠摝坫存在，您可以使用[CMFCAcceleratorKeyAssignCtrl::GetAccel](#getaccel)方法，以取得`ACCEL`這個快顯索引鍵相關聯的結構。  
  
##  <a name="pretranslatemessage"></a>CMFCAcceleratorKeyAssignCtrl::PreTranslateMessage  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
virtual BOOL PreTranslateMessage(MSG* pMsg);
```  
  
### <a name="parameters"></a>參數  
 [輸入] `pMsg`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="resetkey"></a>CMFCAcceleratorKeyAssignCtrl::ResetKey  
 重設快速鍵。  
  
```  
void ResetKey();
```  
  
### <a name="remarks"></a>備註  
 此函式會清除編輯控制項的文字。 這包括使用者按下任何快速鍵。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCAcceleratorKey 類別](../../mfc/reference/cmfcacceleratorkey-class.md)

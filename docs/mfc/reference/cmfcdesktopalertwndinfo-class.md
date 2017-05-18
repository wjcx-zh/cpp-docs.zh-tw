---
title: "CMFCDesktopAlertWndInfo 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_hIcon
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_nURLCmdID
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strText
- AFXDESKTOPALERTDIALOG/CMFCDesktopAlertWndInfo::m_strURL
dev_langs:
- C++
helpviewer_keywords:
- CMFCDesktopAlertWndInfo class
ms.assetid: 5c9bb84e-6c96-4748-8e74-6951b6ae8e84
caps.latest.revision: 26
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 7013a7c9b29c6dc9e6324ca0490a667ed79c88f7
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cmfcdesktopalertwndinfo-class"></a>CMFCDesktopAlertWndInfo 類別
`CMFCDesktopAlertWndInfo`類別搭配[CMFCDesktopAlertWnd 類別](../../mfc/reference/cmfcdesktopalertwnd-class.md)。 這會指定如果桌面警示視窗出現時要顯示的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
class CMFCDesktopAlertWndInfo  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|`CMFCDesktopAlertWndInfo::~CMFCDesktopAlertWndInfo`|解構函式。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::operator =](#operator_eq)||  
  
### <a name="data-members"></a>資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)|控制代碼時所顯示的圖示。|  
|[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)|桌面警示視窗上的連結相關聯的命令識別碼。|  
|[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)|顯示桌面警示視窗的文字。|  
|[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)|會顯示在桌面警示視窗中的連結。|  
  
## <a name="remarks"></a>備註  
 `CMFCDesktopAlertWndInfo`類別傳遞給[CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法，以指定顯示在桌面警示視窗的 [預設] 對話方塊的項目。 [預設] 對話方塊中可以包含三個項目︰  
  
-   圖示，它會藉由呼叫設定[CMFCDesktopAlertWndInfo::m_hIcon](#m_hicon)。  
  
-   標籤或文字訊息，藉由呼叫設定[CMFCDesktopAlertWndInfo::m_strText](#m_strtext)。  
  
-   藉由呼叫設定連結[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)。 若要在按一下連結時，所執行的命令，呼叫[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)。  
  
 如果預設對話方塊不足夠，您可以建立自訂的對話方塊，並將它傳遞給[CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)方法，而不要使用這個類別。 如需詳細資訊，請參閱[CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何使用各種成員`CMFCDesktopAlertWndInfo`類別。 範例會示範如何將控制代碼設定為所顯示的圖示時，會顯示在桌面警示視窗，顯示在桌面警示視窗中，連結和桌面警示視窗上的連結相關聯的命令 ID 的文字。 這個範例是屬於[桌面警示示範範例](../../visual-cpp-samples.md)。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo #&3;](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwndinfo-class_1.cpp)]  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CMFCDesktopAlertWndInfo](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxDesktopAlertDialog.h  
  
##  <a name="operator_eq"></a>CMFCDesktopAlertWndInfo::operator =  
 [!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
```  
CMFCDesktopAlertWndInfo& operator=(CMFCDesktopAlertWndInfo& src);
```  
  
### <a name="parameters"></a>參數  
 [in] `src`  
  
### <a name="return-value"></a>傳回值  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_hicon"></a>CMFCDesktopAlertWndInfo::m_hIcon  
 控制代碼時所顯示的圖示。  
  
```  
HICON m_hIcon;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_nurlcmdid"></a>CMFCDesktopAlertWndInfo::m_nURLCmdID  
 桌面警示視窗上的連結相關聯的命令識別碼。  
  
```  
UINT m_nURLCmdID;  
```  
  
### <a name="remarks"></a>備註  
 當使用者按一下連結所指定的命令 ID 傳送至快顯視窗的擁有者[CMFCDesktopAlertWndInfo::m_strURL](#m_strurl)。  
  
##  <a name="m_strtext"></a>CMFCDesktopAlertWndInfo::m_strText  
 顯示桌面警示視窗的文字。  
  
```  
CString m_strText;  
```  
  
### <a name="remarks"></a>備註  
  
##  <a name="m_strurl"></a>CMFCDesktopAlertWndInfo::m_strURL  
 會顯示在桌面警示視窗中的連結。  
  
```  
CString m_strURL;  
```  
  
### <a name="remarks"></a>備註  
 當使用者按一下連結時，此命令有[CMFCDesktopAlertWndInfo::m_nURLCmdID](#m_nurlcmdid)命令便會傳送快顯視窗的擁有者。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCDesktopAlertWnd 類別](../../mfc/reference/cmfcdesktopalertwnd-class.md)   
 [CMFCDesktopAlertWnd::Create](../../mfc/reference/cmfcdesktopalertwnd-class.md#create)   
 [CMFCDesktopAlertDialog 類別](../../mfc/reference/cmfcdesktopalertdialog-class.md)


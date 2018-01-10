---
title: "CDataExchange 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataExchange
- AFXWIN/CDataExchange
- AFXWIN/CDataExchange::CDataExchange
- AFXWIN/CDataExchange::Fail
- AFXWIN/CDataExchange::PrepareCtrl
- AFXWIN/CDataExchange::PrepareEditCtrl
- AFXWIN/CDataExchange::PrepareOleCtrl
- AFXWIN/CDataExchange::m_bSaveAndValidate
- AFXWIN/CDataExchange::m_pDlgWnd
dev_langs: C++
helpviewer_keywords:
- CDataExchange [MFC], CDataExchange
- CDataExchange [MFC], Fail
- CDataExchange [MFC], PrepareCtrl
- CDataExchange [MFC], PrepareEditCtrl
- CDataExchange [MFC], PrepareOleCtrl
- CDataExchange [MFC], m_bSaveAndValidate
- CDataExchange [MFC], m_pDlgWnd
ms.assetid: 84ed6113-325d-493e-a75d-223f03a992b8
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e56df3ec4604a02ba9cf1075152a11eefe7e28f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cdataexchange-class"></a>CDataExchange 類別
支援 Microsoft Foundation 類別使用的對話方塊資料交換 (DDX) 和對話方塊資料驗證 (DDV) 常式。  
  
## <a name="syntax"></a>語法  
  
```  
class CDataExchange  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDataExchange::CDataExchange](#cdataexchange)|建構 `CDataExchange` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CDataExchange::Fail](#fail)|驗證失敗時呼叫。 將焦點重設為上一個控制項，並擲回例外狀況。|  
|[CDataExchange::PrepareCtrl](#preparectrl)|準備資料交換 」 或 「 驗證指定的控制項。 Nonedit 控制項使用。|  
|[CDataExchange::PrepareEditCtrl](#prepareeditctrl)|準備指定的編輯控制項進行資料交換或驗證作業。|  
|[CDataExchange::PrepareOleCtrl](#prepareolectrl)|準備資料交換 」 或 「 驗證指定的 OLE 控制項。 Nonedit 控制項使用。|  
  
### <a name="public-data-members"></a>公用資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[CDataExchange::m_bSaveAndValidate](#m_bsaveandvalidate)|DDX 和 DDV 方向旗標。|  
|[CDataExchange::m_pDlgWnd](#m_pdlgwnd)|其中的資料交換的對話方塊或視窗會發生。|  
  
## <a name="remarks"></a>備註  
 `CDataExchange`沒有基底類別。  
  
 使用這個類別，如果您要撰寫資料交換常式的自訂資料類型或控制項，或如果您要撰寫您自己的資料驗證常式。 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊](../../mfc/dialog-boxes.md)。  
  
 A`CDataExchange`物件提供 DDX 和 DDV，才會將所需的內容資訊。 旗標`m_bSaveAndValidate`是**FALSE** DDX 時用於填滿資料成員的對話方塊控制項的初始值。 旗標`m_bSaveAndValidate`是**TRUE** DDX 時用於設定成資料成員和 DDV 時用於驗證的資料值的對話方塊控制項的目前值。 如果 DDV 驗證失敗，DDV 程序將會顯示訊息方塊，說明輸入的錯誤。 然後會呼叫 DDV 程序**失敗**重新違規的控制項設定焦點，而且會擲回的例外狀況，並停止驗證程序。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDataExchange`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
##  <a name="cdataexchange"></a>CDataExchange::CDataExchange  
 呼叫此成員函式來建構`CDataExchange`物件。  
  
```  
CDataExchange(
    CWnd* pDlgWnd,  
    BOOL bSaveAndValidate);
```  
  
### <a name="parameters"></a>參數  
 *pDlgWnd*  
 包含控制項的父視窗指標。 這通常是[CDialog](../../mfc/reference/cdialog-class.md)-衍生物件。  
  
 `bSaveAndValidate`  
 如果**TRUE**，這個物件會驗證資料，則控制項中的資料寫入至成員。 如果**FALSE**，這個物件將移從成員資料的控制項。  
  
### <a name="remarks"></a>備註  
 建構`CDataExchange`物件自行將額外的資訊儲存在資料交換物件傳遞至您的視窗[CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)成員函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCControlLadenDialog#70](../../mfc/codesnippet/cpp/cdataexchange-class_1.cpp)]  
  
##  <a name="fail"></a>CDataExchange::Fail  
 對話方塊資料驗證 (DDV) 作業失敗時，架構會呼叫此成員函式。  
  
```  
void Fail();
```  
  
### <a name="remarks"></a>備註  
 **失敗**焦點和選取範圍會還原至其驗證失敗 （如果沒有要還原的控制項） 的控制項。 **失敗**然後擲回例外狀況型別的[CUserException](../../mfc/reference/cuserexception-class.md)停止驗證程序。 例外狀況會導致訊息方塊，說明要顯示的錯誤。 DDV 驗證失敗後，使用者可以重新輸入不當控制項中的資料。  
  
 可以呼叫自訂 DDV 常式的實作項**失敗**從其驗證失敗時的常式。  
  
 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊主題](../../mfc/dialog-boxes.md)。  
  
##  <a name="m_bsaveandvalidate"></a>CDataExchange::m_bSaveAndValidate  
 這個旗標表示對話方塊資料交換 (DDX) 作業的方向。  
  
```  
BOOL m_bSaveAndValidate;  
```  
  
### <a name="remarks"></a>備註  
 旗標為非零，如果`CDataExchange`物件用來將資料從移對話方塊控制項到對話方塊類別資料成員之後使用者編輯控制項。 旗標為零，如果使用物件來初始化從對話方塊類別資料成員的對話方塊控制項。  
  
 旗標也是在對話方塊資料驗證 (DDV) 則為非零。  
  
 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊主題](../../mfc/dialog-boxes.md)。  
  
##  <a name="m_pdlgwnd"></a>CDataExchange::m_pDlgWnd  
 包含的指標[CWnd](../../mfc/reference/cwnd-class.md)的對話方塊資料交換 (DDX) 或驗證 (DDV) 正在進行中的物件。  
  
```  
CWnd* m_pDlgWnd;  
```  
  
### <a name="remarks"></a>備註  
 此物件通常是[CDialog](../../mfc/reference/cdialog-class.md)物件。 自訂的 DDX 或 DDV 常式的實作項可以使用這個指標，以取得存取權的對話方塊視窗包含的控制項操作。  
  
 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊主題](../../mfc/dialog-boxes.md)。  
  
##  <a name="preparectrl"></a>CDataExchange::PrepareCtrl  
 架構會呼叫此成員函式，準備指定之控制項的對話方塊資料交換 (DDX) 和驗證 (DDV)。  
  
```  
HWND PrepareCtrl(int nIDC);
```  
  
### <a name="parameters"></a>參數  
 `nIDC`  
 準備的 DDX 或 DDV 控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 `HWND` DDX 或 DDV 正在準備的控制項。  
  
### <a name="remarks"></a>備註  
 使用[PrepareEditCtrl](#prepareeditctrl)改為編輯控制項; 使用此成員函式為所有其他控制項。  
  
 準備包含儲存控制項的`HWND`中`CDataExchange`類別。 架構會將焦點還原至先前焦點的控制項，DDX 或 DDV 失敗時使用此控制代碼。  
  
 自訂的 DDX 或 DDV 常式的實作項應該呼叫`PrepareCtrl`對所有非編輯控制項，它們會交換資料透過 DDX 或驗證資料透過 DDV。  
  
 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊主題](../../mfc/dialog-boxes.md)。  
  
##  <a name="prepareeditctrl"></a>CDataExchange::PrepareEditCtrl  
 架構會呼叫此成員函式，以準備指定的編輯控制項的對話方塊資料交換 (DDX) 和驗證 (DDV)。  
  
```  
HWND PrepareEditCtrl(int nIDC);
```  
  
### <a name="parameters"></a>參數  
 `nIDC`  
 準備的 DDX 或 DDV 編輯控制項的識別碼。  
  
### <a name="return-value"></a>傳回值  
 `HWND` DDX 或 DDV 正在準備的編輯控制項。  
  
### <a name="remarks"></a>備註  
 使用[PrepareCtrl](#preparectrl)改為針對所有非編輯控制項。  
  
 準備包含兩件事。 首先，`PrepareEditCtrl`儲存控制項的`HWND`中`CDataExchange`類別。 架構會將焦點還原至先前焦點的控制項，DDX 或 DDV 失敗時使用此控制代碼。 第二個，`PrepareEditCtrl`設定的旗標`CDataExchange`類別，表示要交換的資料，或驗證是編輯控制項的控制項。  
  
 自訂的 DDX 或 DDV 常式的實作項應該呼叫`PrepareEditCtrl`的所有編輯的控制項，它們會交換資料透過 DDX 或驗證資料透過 DDV。  
  
 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊主題](../../mfc/dialog-boxes.md)。  
  
##  <a name="prepareolectrl"></a>CDataExchange::PrepareOleCtrl  
 架構會呼叫此成員函式，準備指定之 OLE 控制項的對話方塊資料交換 (DDX) 和驗證 (DDV)。  
  
```  
COleControlSite* PrepareOleCtrl(int nIDC);
```  
  
### <a name="parameters"></a>參數  
 `nIDC`  
 備妥，DDX 或 DDV OLE 控制項 ID。  
  
### <a name="return-value"></a>傳回值  
 OLE 控制項站台指標。  
  
### <a name="remarks"></a>備註  
 使用[PrepareEditCtrl](#prepareeditctrl)改為編輯控制項或[PrepareCtrl](#preparectrl)為所有其他非 OLE 控制項。  
  
 自訂的 DDX 或 DDV 常式的實作項應該呼叫`PrepareOleCtrl`所有 OLE 控制項就會交換資料透過 DDX 或驗證資料透過 DDV。  
  
 如需撰寫您自己的 DDX 和 DDV 常式的詳細資訊，請參閱[技術提示 26](../../mfc/tn026-ddx-and-ddv-routines.md)。 如需 DDX 和 DDV 的概觀，請參閱[對話方塊資料交換和驗證](../../mfc/dialog-data-exchange-and-validation.md)和[對話方塊主題](../../mfc/dialog-boxes.md)。  
  
## <a name="see-also"></a>請參閱  
 [MFC 範例 VIEWEX](../../visual-cpp-samples.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWnd::DoDataExchange](../../mfc/reference/cwnd-class.md#dodataexchange)   
 [CWnd::UpdateData](../../mfc/reference/cwnd-class.md#updatedata)


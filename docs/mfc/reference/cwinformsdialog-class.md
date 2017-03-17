---
title: "CWinFormsDialog 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::CWinFormsDialog
- AFXWINFORMS/CWinFormsDialog::GetControl
- AFXWINFORMS/CWinFormsDialog::GetControlHandle
- AFXWINFORMS/CWinFormsDialog::OnInitDialog
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- CWinFormsDialog class
- Windows Forms [C++], MFC support
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 86768a849b0112f7c4f8b6b2a694b80065169575
ms.lasthandoff: 02/24/2017

---
# <a name="cwinformsdialog-class"></a>CWinFormsDialog 類別
裝載 Windows Form 使用者控制項的 MFC 對話方塊類別包裝函式。  
  
## <a name="syntax"></a>語法  
  
```  
template <typename TManagedControl>  
class CWinFormsDialog :   
    public CDialog  
```  
  
#### <a name="parameters"></a>參數  
 `TManagedControl`  
 .NET Framework 的使用者控制項在 MFC 應用程式中顯示。  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|建構 `CWinFormsDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|擷取至 Windows Form 使用者控制項的參考。|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|擷取 Windows Form 使用者控制項的視窗控制代碼。|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|初始化 MFC 對話方塊中建立和裝載 Windows Form 使用者控制項上。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|取代[CWinFormsDialog::GetControl](#getcontrol)運算式中。|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|將型別轉換成 Windows Form 使用者控制項的參考。|  
  
## <a name="remarks"></a>備註  
 `CWinFormsDialog`是的 MFC 對話方塊類別包裝函式 ( [CDialog](../../mfc/reference/cdialog-class.md)) 裝載 Windows Form 使用者控制項。 這可讓.NET Framework 上的控制項獨佔式或非強制回應的 MFC 對話方塊中顯示。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)和[裝載成 MFC 對話方塊的 Windows Form 使用者控制項](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>CWinFormsDialog::CWinFormsDialog  
 建構 `CWinFormsDialog` 物件。  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>參數  
 `nIDTemplate`  
 包含 ID 的對話方塊範本資源。 使用對話方塊編輯器建立對話方塊範本，並將它儲存在應用程式的資源指令碼檔案。 如需有關對話方塊範本的詳細資訊，請參閱[CDialog 類別](../../mfc/reference/cdialog-class.md)。  
  
##  <a name="getcontrol"></a>CWinFormsDialog::GetControl  
 擷取至 Windows Form 使用者控制項的參考。  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回在 MFC 對話方塊中的 Windows Form 控制項的參考。  
  
##  <a name="getcontrolhandle"></a>CWinFormsDialog::GetControlHandle  
 擷取 Windows Form 使用者控制項的視窗控制代碼。  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回至 Windows Form 使用者控制項的視窗控制代碼。  
  
##  <a name="oninitdialog"></a>CWinFormsDialog::OnInitDialog  
 初始化 MFC 對話方塊中建立和裝載 Windows Form 使用者控制項上。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>傳回值  
 布林值，指定是否應用程式已設定輸入的焦點的控制項在對話方塊中。 如果`OnInitDialog`傳回非零值，Windows 將輸入的焦點設為第一個控制項在對話方塊中。 只有當應用程式已明確設定輸入的焦點之控制項的其中一個對話方塊中，這個方法可以傳回 0。  
  
### <a name="remarks"></a>備註  
 MFC 對話方塊中建立時 (使用[建立](../../mfc/reference/cdialog-class.md#create)， [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)，或[DoModal](../../mfc/reference/cdialog-class.md#domodal)方法繼承自[CDialog](../../mfc/reference/cdialog-class.md))、`WM_INITDIALOG`傳送訊息，且會呼叫這個方法。 它會建立 Windows Form 控制項在對話方塊中的執行個體，並調整大小以配合使用者控制項的大小 對話方塊。 然後它會裝載新的控制項在 MFC 對話方塊中。  
  
 如果您需要執行特殊處理初始化對話方塊時，覆寫此成員函式。 如需有關如何使用此方法的詳細資訊，請參閱[CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)。  
  
##  <a name="operator_-_gt"></a>CWinFormsDialog::operator-&gt;  
 取代[CWinFormsDialog::GetControl](#getcontrol)運算式中。  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>備註  
 此運算子會提供方便的語法，以取代`GetControl`運算式中。  
  
 如需使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_tmanagedcontrol_xor"></a>CWinFormsDialog::operator TManagedControl ^  
 將型別轉換成 Windows Form 使用者控制項的參考。  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>備註  
 這個運算子會將型別轉換成 Windows Form 控制項的參考。 它用來傳遞`CWinFormsDialog<``TManagedControl``>`] 對話方塊中，接受 [Windows Form 使用者控制項物件的指標的函式。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)


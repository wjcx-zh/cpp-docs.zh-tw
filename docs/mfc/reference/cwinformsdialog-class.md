---
title: CWinFormsDialog 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
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
- CWinFormsDialog [MFC], CWinFormsDialog
- CWinFormsDialog [MFC], GetControl
- CWinFormsDialog [MFC], GetControlHandle
- CWinFormsDialog [MFC], OnInitDialog
ms.assetid: e3cec000-a578-448e-b06a-8af256312f61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b7596140f48b62a63189444bee6fb363552766fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371555"
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
 要顯示在 MFC 應用程式的.NET Framework 使用者控制項。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinFormsDialog::CWinFormsDialog](#cwinformsdialog)|建構 `CWinFormsDialog` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinFormsDialog::GetControl](#getcontrol)|擷取 Windows Form 使用者控制項的參考。|  
|[CWinFormsDialog::GetControlHandle](#getcontrolhandle)|擷取 Windows Form 使用者控制項的視窗控制代碼。|  
|[CWinFormsDialog::OnInitDialog](#oninitdialog)|初始化 MFC 對話方塊中建立和裝載在其上的 Windows Form 使用者控制項。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱||  
|----------|-|  
|[CWinFormsDialog::operator-&gt;](#operator_-_gt)|取代[CWinFormsDialog::GetControl](#getcontrol)運算式中。|  
|[CWinFormsDialog::operator TManagedControl ^](#operator_tmanagedcontrol)|將類型轉換成 Windows Form 使用者控制項的參考。|  
  
## <a name="remarks"></a>備註  
 `CWinFormsDialog` 是的 MFC 對話方塊類別包裝函式 ( [CDialog](../../mfc/reference/cdialog-class.md)) 裝載 Windows Form 使用者控制項。 這可讓.NET Framework 上的控制項獨佔式或非強制回應的 MFC 對話方塊中顯示。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)和[裝載為 MFC 對話方塊的 Windows Form 使用者控制項](../../dotnet/hosting-a-windows-form-user-control-as-an-mfc-dialog-box.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h  
  
##  <a name="cwinformsdialog"></a>  CWinFormsDialog::CWinFormsDialog  
 建構 `CWinFormsDialog` 物件。  
  
```  
CWinFormsDialog(UINT nIDTemplate = IDD);
```  
  
### <a name="parameters"></a>參數  
 `nIDTemplate`  
 包含的對話方塊範本資源的識別碼。 使用對話方塊編輯器建立對話方塊範本，並將其儲存在應用程式的資源指令碼檔案。 如需有關對話方塊範本的詳細資訊，請參閱[CDialog 類別](../../mfc/reference/cdialog-class.md)。  
  
##  <a name="getcontrol"></a>  CWinFormsDialog::GetControl  
 擷取 Windows Form 使用者控制項的參考。  
  
```  
inline TManagedControl^ GetControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回的參考加入 Windows Form 控制項 [MFC] 對話方塊中。  
  
##  <a name="getcontrolhandle"></a>  CWinFormsDialog::GetControlHandle  
 擷取 Windows Form 使用者控制項的視窗控制代碼。  
  
```  
inline HWND GetControlHandle() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 Windows Form 使用者控制項的視窗控制代碼。  
  
##  <a name="oninitdialog"></a>  CWinFormsDialog::OnInitDialog  
 初始化 MFC 對話方塊中建立和裝載在其上的 Windows Form 使用者控制項。  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>傳回值  
 布林值，指定應用程式已設輸入的焦點的控制項在對話方塊中。 如果`OnInitDialog`傳回非零，Windows 將輸入的焦點設定到第一個控制項在對話方塊中。 只有當應用程式已明確設定輸入的焦點為其中一個控制項在對話方塊中，這個方法可以傳回 0。  
  
### <a name="remarks"></a>備註  
 MFC 對話方塊中建立時 (使用[建立](../../mfc/reference/cdialog-class.md#create)， [CreateIndirect](../../mfc/reference/cdialog-class.md#createindirect)，或[DoModal](../../mfc/reference/cdialog-class.md#domodal)方法繼承自[CDialog](../../mfc/reference/cdialog-class.md))， `WM_INITDIALOG`傳送訊息，且在呼叫這個方法。 它會建立 Windows Form 控制項在對話方塊中的執行個體，並調整大小以配合使用者控制項的大小 對話方塊。 然後它會裝載新的控制項 [MFC] 對話方塊中。  
  
 如果您需要執行特殊處理對話方塊中初始化時，請覆寫此成員函式。 如需有關如何使用這個方法的詳細資訊，請參閱[CDialog::OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)。  
  
##  <a name="operator_-_gt"></a>  CWinFormsDialog::operator-&gt;  
 取代[CWinFormsDialog::GetControl](#getcontrol)運算式中。  
  
```  
inline TManagedControl^  operator->() const throw();
```  
  
### <a name="remarks"></a>備註  
 這個運算子會提供方便的語法，以取代`GetControl`運算式中。  
  
 如需使用 Windows Form 的資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_tmanagedcontrol_xor"></a>  CWinFormsDialog::operator TManagedControl ^  
 將類型轉換成 Windows Form 使用者控制項的參考。  
  
```  
inline operator TManagedControl^() const throw();
```  
  
### <a name="remarks"></a>備註  
 這個運算子會將類型轉換成 Windows Form 控制項的參考。 用來傳遞`CWinFormsDialog<TManagedControl>`對話方塊中，接受 Windows Form 使用者控制項物件的指標的函式。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)   
 [CDialog 類別](../../mfc/reference/cdialog-class.md)

---
title: "CWinFormsView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs:
- C++
helpviewer_keywords:
- MFC [C++], Windows Forms support
- CWinFormsView class
- Windows Forms [C++], MFC support
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
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
ms.sourcegitcommit: 6c49d711da747e4c6cbad0f883d93196b6a98057
ms.openlocfilehash: 7aadcc1aa887cb6be1ddbb8f3797c4a9e1af5b6a
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cwinformsview-class"></a>CWinFormsView 類別
提供可將 Windows Form 控制項裝載為 MFC 檢視的一般功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CWinFormsView : public CView;  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinFormsView::CWinFormsView](#cwinformsview)|建構 `CWinFormsView` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWinFormsView::GetControl](#getcontrol)|擷取 Windows Form 控制項的指標。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱||  
|----------|-|  
|[CWinFormsView::operator 控制 ^](#operator_control)|將型別轉換成 Windows Form 控制項的指標。|  
  
## <a name="remarks"></a>備註  
 MFC 使用`CWinFormsView`裝載.NET Framework Windows Form 控制項在 MFC 檢視類別。 控制項是子系的原生的檢視，而且會佔用整個工作區的 MFC 檢視。 結果就像`CFormView`檢視，可讓您充分利用 Windows Form 設計工具和執行時間來建立豐富的以 form 為基礎的檢視。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
> [!NOTE]
>  MFC Windows Form 整合只能在動態連結與 MFC 專案中的工作 （AFXDLL 定義所在的專案）。  
  
> [!NOTE]
>  CWinFormsView 不支援 MFC 分隔視窗 ( [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md))。 目前只有 Windows Form 分隔器支援控制項。  
  
## <a name="requirements"></a>需求  
 **標頭︰** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 建構 `CWinFormsView` 物件。  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>參數  
 `pManagedViewType`  
 Windows Form 使用者控制項的資料類型的指標。   
  
### <a name="example"></a>範例  
 在下列範例中，`CUserView`類別繼承自`CWinFormsView`，並傳遞的型別`UserControl1`至`CWinFormsView`建構函式。 `UserControl1`是 ControlLibrary1.dll 自訂控制項。  
  
 [!code-cpp[NVC_MFC_Managed #&1;](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed #&2;](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>CWinFormsView::GetControl  
 擷取 Windows Form 控制項的指標。  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`System.Windows.Forms.Control`物件。  
  
### <a name="remarks"></a>備註  
 如需如何使用 Windows Form 的範例，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_control"></a>CWinFormsView::operator 控制 ^  
 將型別轉換成 Windows Form 控制項的指標。  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>備註  
 這個運算子可讓您傳遞`CWinFormsView`檢視，以接受 Windows Form 控制項的型別<xref:System.Windows.Forms.Control>.</xref:System.Windows.Forms.Control>指標的函式  
  
### <a name="example"></a>範例  
  請參閱[CWinFormsView::GetControl](#getcontrol)。  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl 類別](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView 類別](../../mfc/reference/cformview-class.md)


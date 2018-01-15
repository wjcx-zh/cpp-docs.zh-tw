---
title: "CWinFormsView 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWinFormsView
- AFXWINFORMS/CWinFormsView
- AFXWINFORMS/CWinFormsView::CWinFormsView
- AFXWINFORMS/CWinFormsView::GetControl
dev_langs: C++
helpviewer_keywords:
- CWinFormsView [MFC], CWinFormsView
- CWinFormsView [MFC], GetControl
ms.assetid: d597e397-6529-469b-88f5-7f65a6b9e895
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cb68e906a06d18b41d97851d8d91717ac3dd78b3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="cwinformsview-class"></a>CWinFormsView 類別
提供可將 Windows Form 控制項裝載為 MFC 檢視的一般功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CWinFormsView : public CView;  
```  
  
## <a name="members"></a>成員  
  
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
|[CWinFormsView::operator 控制項 ^](#operator_control)|將類型轉換成 Windows Form 控制項的指標。|  
  
## <a name="remarks"></a>備註  
 MFC 使用`CWinFormsView`裝載.NET Framework Windows Form 控制項在 MFC 檢視的類別。 控制項子系的原生的檢視，而且佔滿 MFC 檢視的整個工作區。 結果會類似於`CFormView`檢視，可讓您充分利用 Windows Form 設計工具和執行階段建立表單架構的豐富檢視。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
> [!NOTE]
>  MFC Windows Form 整合的工作只能在動態連結與 MFC 專案中 （AFXDLL 定義所在的專案）。  
  
> [!NOTE]
>  CWinFormsView 不支援 MFC 分隔視窗 ( [CSplitterWnd 類別](../../mfc/reference/csplitterwnd-class.md))。 目前只有 Windows Form 分隔器支援控制。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxwinforms.h  
  
##  <a name="cwinformsview"></a>CWinFormsView::CWinFormsView  
 建構 `CWinFormsView` 物件。  
  
```  
CWinFormsView(System::Type^ pManagedViewType);  
```  
  
### <a name="parameters"></a>參數  
 `pManagedViewType`  
 Windows Form 使用者控制項的資料類型的指標。   
  
### <a name="example"></a>範例  
 在下列範例中，`CUserView`類別繼承自`CWinFormsView`，並將傳遞的型別`UserControl1`至`CWinFormsView`建構函式。 `UserControl1`是 ControlLibrary1.dll 自訂控制項。  
  
 [!code-cpp[NVC_MFC_Managed#1](../../mfc/reference/codesnippet/cpp/cwinformsview-class_1.h)]  
  
 [!code-cpp[NVC_MFC_Managed#2](../../mfc/reference/codesnippet/cpp/cwinformsview-class_2.cpp)]  
  
##  <a name="getcontrol"></a>CWinFormsView::GetControl  
 擷取 Windows Form 控制項的指標。  
  
```  
System::Windows::Forms::Control^ GetControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標`System.Windows.Forms.Control`物件。  
  
### <a name="remarks"></a>備註  
 如需如何使用 Windows Form 的範例，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  
##  <a name="operator_control"></a>CWinFormsView::operator 控制項 ^  
 將類型轉換成 Windows Form 控制項的指標。  
  
```  
operator System::Windows::Forms::Control^() const;  
```  
  
### <a name="remarks"></a>備註  
 這個運算子可讓您傳遞`CWinFormsView`接受類型的 Windows Form 控制項的指標的函式檢視<xref:System.Windows.Forms.Control>。  
  
### <a name="example"></a>範例  
  請參閱[CWinFormsView::GetControl](#getcontrol)。  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CWinFormsControl 類別](../../mfc/reference/cwinformscontrol-class.md)   
 [CWinFormsDialog 類別](../../mfc/reference/cwinformsdialog-class.md)   
 [CFormView 類別](../../mfc/reference/cformview-class.md)

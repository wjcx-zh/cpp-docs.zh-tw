---
title: IView 介面 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IView
- AFXWINFORMS/IView
- AFXWINFORMS/IView::OnActivateView
- AFXWINFORMS/IView::OnInitialUpdate
- AFXWINFORMS/IView::OnUpdate
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class [MFC]
- views [MFC], classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a06243af3de7a2f4b32aa9a9ae492dfe3b2d3b64
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370955"
---
# <a name="iview-interface"></a>IView 介面
實作數個方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)使用將檢視通知傳送到受管理的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
interface class IView  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|由 MFC 檢視為啟用或停用時呼叫。|  
|[IView::OnInitialUpdate](#oninitialupdate)|檢視第一次連接到文件，但最初顯示在檢視之前由架構呼叫。|  
|[IView::OnUpdate](#onupdate)|修改檢視的文件; 之後，由 MFC 呼叫此函式可更新以反映修改顯示的檢視。|  
  
## <a name="remarks"></a>備註  
 `IView` 實作數個方法，`CWinFormsView`使用轉送至裝載 managed 控制項的一般檢視通知。 這些是[OnInitialUpdate](#oninitialupdate)， [OnUpdate](#onupdate)和[OnActivateView](#onactivateview)。  
  
 `IView` 類似於[CView](../../mfc/reference/cview-class.md)，但是只適用於受管理的檢視及控制項。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  

## <a name="requirements"></a>需求  
 標頭： afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  

## <a name="onactivateview"></a> IView::OnActivateView  
由 MFC 檢視為啟用或停用時呼叫。
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>參數
`activate`  
代表是否要檢視啟用或停用。  

## <a name="oninitialupdate"></a> IView::OnInitialUpdate
檢視第一次連接到文件，但最初顯示在檢視之前由架構呼叫。
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate 
修改檢視的文件之後，由 MFC 呼叫。  
```
void OnUpdate();
```
## <a name="remarks"></a>備註  
此函式可更新以反映修改顯示的檢視。

## <a name="see-also"></a>另請參閱  
 [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)

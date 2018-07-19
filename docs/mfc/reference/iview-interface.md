---
title: IView 介面 |Microsoft Docs
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
ms.openlocfilehash: acf1ba02e9bbf6afd14e41be7dda406d257cb681
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37339757"
---
# <a name="iview-interface"></a>IView 介面
會實作數個方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)使用將檢視通知傳送至受管理的控制項。  
  
## <a name="syntax"></a>語法  
  
```  
interface class IView  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|啟用或停用檢視時，由 MFC 呼叫。|  
|[IView::OnInitialUpdate](#oninitialupdate)|檢視第一次附加至文件之後，但一開始顯示檢視之前，由架構呼叫。|  
|[IView::OnUpdate](#onupdate)|修改檢視的文件; 之後，由 MFC 呼叫此函式可讓更新以反映修改其顯示的檢視。|  
  
## <a name="remarks"></a>備註  
 `IView` 會實作數個方法，`CWinFormsView`使用轉送至裝載 managed 控制項的一般檢視通知。 這些是[OnInitialUpdate](#oninitialupdate)， [OnUpdate](#onupdate)並[OnActivateView](#onactivateview)。  
  
 `IView` 類似於[CView](../../mfc/reference/cview-class.md)，但僅適用於受管理的檢視和控制。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱 <<c0> [ 在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  

## <a name="requirements"></a>需求  
 標頭： afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  

## <a name="onactivateview"></a> IView::OnActivateView  
啟用或停用檢視時，由 MFC 呼叫。
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>參數
*啟用*  
表示正在檢視是否啟用或停用。  

## <a name="oninitialupdate"></a> IView::OnInitialUpdate
檢視第一次附加至文件之後，但一開始顯示檢視之前，由架構呼叫。
```
void OnInitialUpdate();
```

## <a name="onupdate"></a> IView::OnUpdate 
修改檢視的文件之後，由 MFC 呼叫。  
```
void OnUpdate();
```
## <a name="remarks"></a>備註  
此函式可讓更新以反映修改其顯示的檢視。

## <a name="see-also"></a>另請參閱  
 [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)

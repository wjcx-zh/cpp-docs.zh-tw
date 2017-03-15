---
title: "IView 介面 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IView
dev_langs:
- C++
helpviewer_keywords:
- views [MFC]
- IView class
- views, classes
ms.assetid: 9321f299-486e-4551-bee9-d2c4a7b91548
caps.latest.revision: 23
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 9a8b5f2d9d123aa3032cb30ecdbdd1cd380b32f8
ms.lasthandoff: 02/24/2017

---
# <a name="iview-interface"></a>IView 介面
實作數個方法， [CWinFormsView](../../mfc/reference/cwinformsview-class.md)檢視通知傳送至 managed 控制項使用。  
  
## <a name="syntax"></a>語法  
  
```  
interface class IView  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IView::OnActivateView](#onactivateview)|由 MFC 檢視是啟用或停用時呼叫。|  
|[IView::OnInitialUpdate](#oninitialupdate)|檢視第一次連接到文件之後，但一開始會顯示檢視之前，由架構呼叫。|  
|[IView::OnUpdate](#onupdate)|修改檢視的文件; 之後，由 MFC 呼叫此函式可更新以反映修改顯示的檢視。|  
  
## <a name="remarks"></a>備註  
 `IView`實作數個方法，`CWinFormsView`使用轉送至裝載的 managed 控制項的一般檢視通知。 這些是[OnInitialUpdate](#oninitialupdate)， [OnUpdate](#onupdate)和[OnActivateView](#onactivateview)。  
  
 `IView`類似於[CView](../../mfc/reference/cview-class.md)，但僅適用於受管理的檢視和控制。  
  
 如需有關如何使用 Windows Form 的詳細資訊，請參閱[在 MFC 中使用 Windows Form 使用者控制項](../../dotnet/using-a-windows-form-user-control-in-mfc.md)。  
  

## <a name="requirements"></a>需求  
 標頭︰ afxwinforms.h （定義於組件 atlmfc\lib\mfcmifc80.dll）  

## <a name="a-nameonactivateviewa-iviewonactivateview"></a><a name="onactivateview"></a>IView::OnActivateView  
由 MFC 檢視是啟用或停用時呼叫。
```
void OnActivateView(bool activate);
```
## <a name="parameters"></a>參數
`activate`  
指出檢視是否目前已啟用或停用。  

## <a name="a-nameoninitialupdatea-iviewoninitialupdate"></a><a name="oninitialupdate"></a>IView::OnInitialUpdate
檢視第一次連接到文件之後，但一開始會顯示檢視之前，由架構呼叫。
```
void OnInitialUpdate();
```

## <a name="a-nameonupdatea-iviewonupdate"></a><a name="onupdate"></a>IView::OnUpdate 
修改檢視的文件之後，由 MFC 呼叫。  
```
void OnUpdate();
```
## <a name="remarks"></a>備註  
此函式可更新以反映修改顯示的檢視。

## <a name="see-also"></a>另請參閱  
 [CWinFormsView 類別](../../mfc/reference/cwinformsview-class.md)   
 [CView 類別](../../mfc/reference/cview-class.md)


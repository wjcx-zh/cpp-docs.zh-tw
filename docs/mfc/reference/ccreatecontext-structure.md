---
title: "CCreateContext 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCreateContext
dev_langs:
- C++
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 929ed0971f9b69bf8e98ae247957110e78ac33ba
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ccreatecontext-structure"></a>CCreateContext 結構
架構會使用`CCreateContext`結構時，它會建立框架視窗和文件相關聯的檢視。  
  
## <a name="syntax"></a>語法  
  
```  
struct CCreateContext  
```  
  
## <a name="remarks"></a>備註  
 `CCreateContext`是一種結構，而且沒有基底類別。  
  
 當您建立一個視窗時，此結構中的值會提供用來連接到其資料的檢視的文件的元件的資訊。 您只需要使用`CCreateContext`如果您正在覆寫組件的建立程序。  
  
 A`CCreateContext`結構包含文件、 框架視窗、 檢視和文件範本的指標。 它也包含指向`CRuntimeClass`可識別要建立檢視的類型。 執行階段類別資訊和目前的文件指標可用來動態建立新的檢視。 下表建議的方式和時機每個`CCreateContext`成員可能會使用：  
  
|成員|類型|是用於|  
|------------|----------|--------------------|  
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`若要建立新的檢視。|  
|`m_pCurrentDoc`|`CDocument*`|要與新的檢視相關聯的現有文件。|  
|`m_pNewDocTemplate`|`CDocTemplate*`|建立新的 MDI 框架視窗相關聯的文件範本。|  
|`m_pLastView`|`CView*`|原始檢視的其他檢視建立模型，如同建立分隔視窗中檢視或建立的文件上的第二個檢視。|  
|`m_pCurrentFrame`|`CFrameWnd*`|框架視窗的其他框架視窗建立模型，如同第二個文件框架視窗的建立。|  
  
 當文件範本建立文件及相關的元件時，它會驗證資訊儲存在`CCreateContext`結構。 例如，檢視不應建立不存在的文件。  
  
> [!NOTE]
>  所有在指標`CCreateContext`是選擇性的而且可以是`NULL`如果未指定或未知。  
  
 `CCreateContext`底下列出的成員函式由 「 另請參閱。 」 如果想要覆寫它們，請參閱這些函式描述的特定資訊。  
  
 以下是一些一般指導方針：  
  
-   在為視窗建立的引數傳遞時`CWnd::Create`， `CFrameWnd::Create`，和`CFrameWnd::LoadFrame`，建立內容可讓您指定什麼新的視窗應該連接到。 對於大部分的 windows，整個結構是選擇性和`NULL`可以傳遞指標。  
  
-   可覆寫成員函式，例如`CFrameWnd::OnCreateClient`、`CCreateContext`引數是選擇性。  
  
-   成員函式相關檢視中建立，您必須提供足夠的資訊來建立檢視。 比方說，在分隔視窗中的第一個檢視，您必須提供的檢視類別資訊和目前的文件。  
  
 一般情況下，如果您使用 framework 的預設值，您可以忽略`CCreateContext`。 如果您嘗試使用更進階的修改、 Microsoft Foundation 類別庫原始碼或範例程式，例如 VIEWEX，將引導您。 如果您不要忘記的必要的參數，架構判斷提示會告訴您忘了。  
  
 如需有關`CCreateContext`，請參閱 MFC 範例[VIEWEX](../../visual-cpp-samples.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** afxext.h  
  
## <a name="see-also"></a>請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)   
 [CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)   
 [CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)   
 [CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)   
 [CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)   
 [Cwnd:: Create](../../mfc/reference/cwnd-class.md#create)


---
title: CCreateContext 結構
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 795b20cba41eeca8cc1a32e312edf065b718f364
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58768482"
---
# <a name="ccreatecontext-structure"></a>CCreateContext 結構

架構會使用`CCreateContext`結構時建立框架視窗和文件相關聯的檢視。

## <a name="syntax"></a>語法

```
struct CCreateContext
```

## <a name="remarks"></a>備註

`CCreateContext` 是一種結構，而且沒有基底類別。

當您建立視窗時，此結構中的值會提供用來連接到其資料檢視的文件的元件的資訊。 您只需要使用`CCreateContext`如果您正在覆寫組件的建立程序。

A`CCreateContext`結構包含文件、 框架視窗、 檢視和文件範本的指標。 它也包含一個指向`CRuntimeClass`可識別要建立的檢視類型。 執行階段類別資訊，並將目前的文件指標用來以動態方式建立新的檢視。 下表會建議如何及何時每`CCreateContext`成員可能會使用：

|成員|類型|它為|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` 若要建立新的檢視。|
|`m_pCurrentDoc`|`CDocument*`|要與新的檢視相關聯的現有文件。|
|`m_pNewDocTemplate`|`CDocTemplate*`|建立新的 MDI 框架視窗相關聯的文件範本。|
|`m_pLastView`|`CView*`|原始的檢視，在其額外的檢視建立模型，建立分隔器視窗中檢視或建立的文件上的第二個檢視。|
|`m_pCurrentFrame`|`CFrameWnd*`|在其其他框架視窗會建立模型，如所示的文件上的第二個框架視窗建立框架視窗。|

當文件範本建立文件和其相關聯的元件時，它會驗證資訊儲存在`CCreateContext`結構。 例如，檢視不應建立不存在的文件。

> [!NOTE]
>  中的指標的所有`CCreateContext`是選擇性的而且可以是`NULL`如果未指定或未知。

`CCreateContext` 底下列出的成員函式會使用 「 另請參閱。 」 如果您打算覆寫它們，則您可以如特定資訊的描述，這些函式。

以下是一些一般指導方針：

- 中傳遞做為引數的視窗建立時`CWnd::Create`， `CFrameWnd::Create`，和`CFrameWnd::LoadFrame`，建立內容可讓您指定什麼新的視窗應該連接到。 對於大部分的視窗中，整個結構是選擇性的`NULL`可以傳遞指標。

- 可覆寫成員函式，例如`CFrameWnd::OnCreateClient`，則`CCreateContext`引數是選擇性。

- 成員函式相關檢視中建立，您必須提供足夠的資訊，以建立檢視。 比方說，如果分隔器視窗中的第一個檢視，您必須提供檢視類別資訊和目前文件。

一般情況下，如果您使用 framework 預設值時，您可以忽略`CCreateContext`。 如果您嘗試使用更進階的修改、 Microsoft Foundation 類別程式庫原始碼或範例程式，例如 VIEWEX，將引導您。 如果您不要忘記必要的參數，framework 判斷提示會告訴您您忘了。

如需詳細資訊`CCreateContext`，請參閱 MFC 範例[VIEWEX](../../overview/visual-cpp-samples.md)。

## <a name="requirements"></a>需求

**標頭：** afxext.h

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)

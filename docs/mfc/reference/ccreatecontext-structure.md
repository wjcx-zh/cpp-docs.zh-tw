---
title: 建立上下課程結構
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 29fc6210b9888b6a5ba5aaf15b66242c29c15dc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369386"
---
# <a name="ccreatecontext-structure"></a>建立上下課程結構

框架在`CCreateContext`創建與文檔關聯的框架視窗和檢視時使用結構。

## <a name="syntax"></a>語法

```
struct CCreateContext
```

## <a name="remarks"></a>備註

`CCreateContext`是一個結構,沒有基類。

創建視窗時,此結構中的值提供用於將文檔元件連接到其數據檢視的資訊。 僅當重寫創建過程的某些部分`CCreateContext`時,才需要使用。

結構`CCreateContext`包含指向文檔、框架視窗、檢視和文件範本的指標。 它還包含指向`CRuntimeClass`標識要創建的檢視類型的指標。 運行時類資訊和當前文件指標用於動態創建新檢視。 下表說明了如何使用以及何時使用每個`CCreateContext`成員:

|member|類型|它的目的是什麼|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass`要創建的新檢視。|
|`m_pCurrentDoc`|`CDocument*`|要與新檢視關聯的現有文檔。|
|`m_pNewDocTemplate`|`CDocTemplate*`|與創建新 MDI 框架視窗關聯的文件範本。|
|`m_pLastView`|`CView*`|對其他檢視建模的原始檢視,如建立拆分視窗檢視或創建文檔上的第二個檢視。|
|`m_pCurrentFrame`|`CFrameWnd*`|對附加框架視窗建模的幀視窗,如在文檔上創建第二個框架視窗。|

當文檔範本創建文檔及其關聯的元件時,它會驗證存儲在結構`CCreateContext`中的資訊。 例如,不應為不存在的文檔創建檢視。

> [!NOTE]
> 中的所有`CCreateContext`指標都是可選的,如果未指定或`NULL`未知,則可以。

`CCreateContext`由「另請參閱」下列出的成員函數使用。 如果您計劃重寫這些函數,請參閱這些函數的說明,瞭解它們的特定資訊。

以下是一些一般準則:

- 當作為視窗創建參數傳遞時,如在`CWnd::Create``CFrameWnd::Create`和`CFrameWnd::LoadFrame`中,創建上下文指定新視窗應連接到的內容。 對於大多數視窗,整個結構是可選的,可以傳遞`NULL`指標。

- 對於可重寫的成員函數(如`CFrameWnd::OnCreateClient``CCreateContext`, 參數是可選的)。

- 對於檢視創建中涉及的成員函數,必須提供足夠的資訊來創建檢視。 例如,對於拆分器視窗中的第一個檢視,必須提供檢視類資訊和當前文檔。

通常,如果使用框架預設值,則可以忽略`CCreateContext`。 如果您嘗試更高級的修改,Microsoft 基礎類庫原始程式碼或示例程式(如 VIEWEX)將指導您。 如果您忘記了所需的參數,框架斷言將告訴您忘記了什麼。

有關 的詳細`CCreateContext`資訊 ,請參閱 MFC 範例[VIEWEX](../../overview/visual-cpp-samples.md)。

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFramewnd::創建](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFramewnd::載入幀](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFramewnd::打開建立用戶端](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterwnd::創建](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterwnd::創建檢視](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)

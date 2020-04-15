---
title: CWaitCursor 類別
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 48ef8f9c965f54deafcc62451639f8c31021e900
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373182"
---
# <a name="cwaitcursor-class"></a>CWaitCursor 類別

可讓您以使用一行程式碼的方式，在執行長時間作業期間顯示等待游標，這通常顯示為沙漏。

## <a name="syntax"></a>語法

```
class CWaitCursor
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CWaitCursor:CWaitCursor](#cwaitcursor)|構造`CWaitCursor`對象並顯示等待游標。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CWaitCursor::恢復](#restore)|更改等待游標后還原它。|

## <a name="remarks"></a>備註

`CWaitCursor`沒有基類。

良好的 Windows 程式設計實踐要求,每當執行需要明顯時間的操作時,都會顯示等待游標。

要顯示等待游標,只需在執行長時間`CWaitCursor`操作的代碼之前定義變數。 對象的建構函數會自動顯示等待游標。

當物件超出範圍(在聲明`CWaitCursor`物件的塊的末尾)時,其析構函數將游標設置到前面的游標。 換句話說,對象會自動執行必要的清理。

> [!NOTE]
> 由於其建構函數和析構函數的工作方式,`CWaitCursor`對象始終聲明為局部變數 - 它們永遠不會聲明為全域變數,也不會使用**new**分配。

如果執行可能導致游標更改的操作(如顯示消息框或對話方塊),請調用[還原](#restore)成員函數以還原等待游標。 即使當前顯示等待游標`Restore`,也可以調用。

顯示等待游標的另一種方法是使用[CCmdTarget:::開始等待游標](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)[,CmdTarget::結束等待游標](../../mfc/reference/ccmdtarget-class.md#endwaitcursor),也許[CMdTarget::還原等待游標](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。 但是,`CWaitCursor`使用起來更容易,因為完成冗長的操作后,不需要將游標設置為上一個游標。

> [!NOTE]
> MFC 使用[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虛擬函數設置和恢復游標。 您可以重寫此函數以提供自定義行為。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CWaitCursor`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor:CWaitCursor

要顯示等待游標,只需在執行長時間`CWaitCursor`操作的代碼之前聲明物件。

```
CWaitCursor();
```

### <a name="remarks"></a>備註

建構函數會自動顯示等待游標。

當物件超出範圍(在聲明`CWaitCursor`物件的塊的末尾)時,其析構函數將游標設置到前面的游標。 換句話說,對象會自動執行必要的清理。

可以利用在塊末尾調用析構函數(可能在函數末尾)這一事實,使等待游標僅在函數的一部分中處於活動狀態。 此技術如下第二個示例所示。

> [!NOTE]
> 由於其建構函數與析構函式的工作方式,`CWaitCursor`物件始終表示, 但部份變數 ──永遠不會聲明為全域變數,也不會使用**新**分配 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor::恢復

要還原等待游標,請在執行操作(如顯示消息框或對話框)後調用此函數,這可能會將等待游標更改為另一個游標。

```
void Restore();
```

### <a name="remarks"></a>備註

即使當前顯示等待游標`Restore`,也可以調用。

如果在聲明`CWaitCursor`物件的函數以外的函數中需要還原等待游標,可以調用[CCmdTarget:::還原WaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CMD目標::開始等待游標](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CmD目標::結束等待游標](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[Cmd目標::恢復等待游標](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::Do等待游標](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[如何操作:更改 Microsoft 基礎類別應用程式中的滑鼠游標](https://go.microsoft.com/fwlink/p/?linkid=128044)

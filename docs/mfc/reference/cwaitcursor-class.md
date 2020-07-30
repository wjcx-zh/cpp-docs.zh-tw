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
ms.openlocfilehash: dfeedad18b3ebcefedff446699f074c86037a4a3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222871"
---
# <a name="cwaitcursor-class"></a>CWaitCursor 類別

可讓您以使用一行程式碼的方式，在執行長時間作業期間顯示等待游標，這通常顯示為沙漏。

## <a name="syntax"></a>語法

```
class CWaitCursor
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|會建立 `CWaitCursor` 物件並顯示等待游標。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CWaitCursor：： Restore](#restore)|在變更之後還原等待游標。|

## <a name="remarks"></a>備註

`CWaitCursor`沒有基類。

良好的 Windows 程式設計實務會要求您在執行需要相當長時間的作業時，顯示等候游標。

若要顯示等待游標，只要在 `CWaitCursor` 執行冗長作業的程式碼之前定義變數即可。 物件的函式會自動導致等候游標顯示。

當物件超出範圍（在宣告物件的區塊結尾處 `CWaitCursor` ）時，其析構函式會將資料指標設定為上一個資料指標。 換句話說，物件會自動執行必要的清除。

> [!NOTE]
> 因為物件的函式和析構函式如何正常執行， `CWaitCursor` 所以一律會將物件宣告為區域變數，這些變數絕不會宣告為全域變數，也不會以配置 **`new`** 。

如果您執行的作業可能會導致資料指標變更（例如顯示訊息方塊或對話方塊），請呼叫[restore](#restore)成員函式來還原等待游標。 `Restore`即使目前正在顯示等候游標，還是可以呼叫。

另一個顯示等待游標的方式，是使用[CCmdTarget：： BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)、 [CCmdTarget：： EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)的組合，以及可能的[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。 不過， `CWaitCursor` 較容易使用，因為當您完成冗長的作業時，不需要將游標設定為上一個資料指標。

> [!NOTE]
> MFC 會使用[CWinApp：:D owaitcursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虛擬函式來設定和還原資料指標。 您可以覆寫此函式，以提供自訂行為。

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CWaitCursor`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

## <a name="cwaitcursorcwaitcursor"></a><a name="cwaitcursor"></a>CWaitCursor::CWaitCursor

若要顯示等待游標，只要在 `CWaitCursor` 執行冗長作業的程式碼之前宣告物件即可。

```
CWaitCursor();
```

### <a name="remarks"></a>備註

此函式會自動導致等候游標顯示。

當物件超出範圍（在宣告物件的區塊結尾處 `CWaitCursor` ）時，其析構函式會將資料指標設定為上一個資料指標。 換句話說，物件會自動執行必要的清除。

您可以利用在區塊結尾呼叫的析構函數（可能是在函式的結尾之前），使等待游標僅供函數的一部分使用。 下列第二個範例會顯示這項技術。

> [!NOTE]
> 因為物件的函式和析構函式如何正常執行，所以 `CWaitCursor` 物件一律會宣告為區域變數，這些變數絕不會宣告為全域變數，也不會使用進行配置 **`new`** 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

## <a name="cwaitcursorrestore"></a><a name="restore"></a>CWaitCursor：： Restore

若要還原等待游標，請在執行作業之後呼叫此函式，例如顯示訊息方塊或對話方塊，這可能會將等候游標變更為另一個資料指標。

```cpp
void Restore();
```

### <a name="remarks"></a>備註

`Restore`即使目前已顯示等候游標，還是可以呼叫。

如果您需要在宣告物件的函式以外的函式中還原等候資料指標 `CWaitCursor` ，您可以呼叫[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget：： BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget：： EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget：： RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp：:D oWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[如何：在 Microsoft Foundation Class 應用程式中變更滑鼠游標](https://go.microsoft.com/fwlink/p/?linkid=128044)

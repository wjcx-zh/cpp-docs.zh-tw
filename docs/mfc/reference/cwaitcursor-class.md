---
title: CWaitCursor 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1e7bc4755d2e96c78735f1b3ef175ff3603686fb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
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
|[CWaitCursor::CWaitCursor](#cwaitcursor)|建構`CWaitCursor`物件，並顯示等待游標。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|已變更之後，還原將等待游標。|  
  
## <a name="remarks"></a>備註  
 `CWaitCursor` 沒有基底類別。  
  
 良好程式設計作法的 Windows 會要求您顯示等待游標，每當您正在執行的作業採用可觀的時間。  
  
 若要顯示等待游標，只定義`CWaitCursor`變數之前執行長時間作業的程式碼。 物件的建構函式會自動讓顯示等待游標。  
  
 當物件超出範圍 (所在的區塊結尾`CWaitCursor`宣告物件)，其解構函式將資料指標設定為先前的資料指標。 換句話說，該物件會自動執行必要的清除。  
  
> [!NOTE]
>  由於其建構函式和解構函式的運作方式，`CWaitCursor`物件一律會宣告為區域變數 — 它們永遠不會宣告為全域變數，也不會以它們配置**新**。  
  
 如果您執行的作業可能會造成變更，例如顯示訊息方塊或對話方塊中，呼叫游標[還原](#restore)成員函式以還原將等待游標。 可以呼叫**還原**甚至等待游標目前顯示時。  
  
 若要使用的組合是另一種方式顯示等待游標[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，也可能[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). 不過，`CWaitCursor`更輕鬆地使用，因為您不需要資料指標設定為先前的資料指標，當您完成長時間作業。  
  
> [!NOTE]
>  MFC 設定並還原資料指標使用[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虛擬函式。 您可以覆寫此函式可提供自訂行為。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CWaitCursor`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor  
 若要顯示等待游標，只宣告`CWaitCursor`之前執行長時間作業的程式碼的物件。  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>備註  
 建構函式會自動讓顯示等待游標。  
  
 當物件超出範圍 (所在的區塊結尾`CWaitCursor`宣告物件)，其解構函式將資料指標設定為先前的資料指標。 換句話說，該物件會自動執行必要的清除。  
  
 您可以利用解構函式呼叫 （這可能是在函式結束之前） 的區塊的結尾，使將等待游標作用的函式的組件中的事實。 這項技術是以下列第二個範例所示。  
  
> [!NOTE]
>  由於其建構函式和解構函式的運作方式，`CWaitCursor`物件一律會宣告為區域變數 — 它們永遠不會宣告為全域變數，也不會以它們配置**新**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>  CWaitCursor::Restore  
 若要還原將等待游標，請執行作業，例如顯示訊息方塊或對話方塊中，可能會將等待游標變更為另一個資料指標之後呼叫此函式。  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>備註  
 呼叫正常**還原**甚至將等待游標目前顯示時。  
  
 如果您需要還原以外，在其中一個函式中的將等待游標`CWaitCursor`宣告物件，您可以呼叫[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [I： 如何變更滑鼠指標在 Microsoft Foundation 類別應用程式](http://go.microsoft.com/fwlink/p/?linkid=128044)




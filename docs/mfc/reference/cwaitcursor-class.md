---
title: "CWaitCursor 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
dev_langs:
- C++
helpviewer_keywords:
- cursors, wait cursor
- CWaitCursor class
- wait cursors
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: f72598c356add5d891b013f1fd7b87665c5a6c63
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="cwaitcursor-class"></a>CWaitCursor 類別
可讓您以使用一行程式碼的方式，在執行長時間作業期間顯示等待游標，這通常顯示為沙漏。  
  
## <a name="syntax"></a>語法  
  
```  
class CWaitCursor  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CWaitCursor::CWaitCursor](#cwaitcursor)|建構`CWaitCursor`物件，並顯示等待游標。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CWaitCursor::Restore](#restore)|已變更之後，還原將等待游標。|  
  
## <a name="remarks"></a>備註  
 `CWaitCursor`沒有基底類別。  
  
 良好的 Windows 程式設計做法需要您顯示等待游標，每當您要執行的作業採用可觀的時間。  
  
 若要顯示等待游標，只需定義`CWaitCursor`變數之前執行長時間作業的程式碼。 物件的建構函式會自動讓顯示等待游標。  
  
 當物件超出範圍 (以區塊的結尾`CWaitCursor`宣告物件)，其解構函式將資料指標設定為先前的資料指標。 換句話說，物件會自動執行必要的清除。  
  
> [!NOTE]
>  其建構函式和解構函式的運作方式，因為`CWaitCursor`物件一律會宣告為區域變數 — 它們永遠不會宣告為全域變數，也不會使用這些配置**新**。  
  
 如果您執行的作業可能會造成資料指標會變更，例如顯示訊息方塊或對話方塊中，呼叫[還原](#restore)成員函式來還原將等待游標。 可以呼叫**還原**甚至當等待游標目前正在顯示。  
  
 若要顯示等待游標的另一個方法是使用的組合[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)， [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)，也可能是[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。 不過，`CWaitCursor`容易使用，因為您不需要長時間作業完成時，將游標放到上一個資料指標。  
  
> [!NOTE]
>  MFC 設定並還原資料指標使用[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)虛擬函式。 您可以覆寫這個函式，以提供自訂行為。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CWaitCursor`  
  
## <a name="requirements"></a>需求  
 **標題:** afxwin.h  
  
## <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&62;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]  
  
##  <a name="cwaitcursor"></a>CWaitCursor::CWaitCursor  
 若要顯示等待游標，只是宣告`CWaitCursor`之前執行長時間作業的程式碼的物件。  
  
```  
CWaitCursor();
```  
  
### <a name="remarks"></a>備註  
 建構函式會自動讓顯示等待游標。  
  
 當物件超出範圍 (以區塊的結尾`CWaitCursor`宣告物件)，其解構函式將資料指標設定為先前的資料指標。 換句話說，物件會自動執行必要的清除。  
  
 您可以利用解構函式呼叫 （這可能是在函式結束之前） 的區塊的結尾，使將等待游標的作用，在函式的組件中的事實。 這項技術是以下列第二個範例所示。  
  
> [!NOTE]
>  其建構函式和解構函式的運作方式，因為`CWaitCursor`物件一律會宣告為區域變數 — 它們永遠不會宣告為全域變數，也不會使用這些配置**新**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&63;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]  
  
##  <a name="restore"></a>CWaitCursor::Restore  
 若要還原將等待游標，請執行作業，例如顯示訊息方塊或對話方塊中，可能會將等待游標變更為另一個資料指標之後呼叫此函式。  
  
```  
void Restore();
```  
  
### <a name="remarks"></a>備註  
 確定要呼叫**還原**甚至將等待游標目前顯示時。  
  
 如果您需要還原在其中一個函式中的將等待游標`CWaitCursor`宣告物件，您可以呼叫[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFCWindowing #&64;](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)   
 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)   
 [CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)   
 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)   
 [I︰ 如何變更 Microsoft Foundation 類別應用程式中的滑鼠游標](http://go.microsoft.com/fwlink/linkid=128044)





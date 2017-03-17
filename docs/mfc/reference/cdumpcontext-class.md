---
title: "CDumpContext 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
dev_langs:
- C++
helpviewer_keywords:
- CDumpContext class
- AfxDump object
- diagnostics, diagnostic classes
- diagnostic classes
- diagnosis, diagnostic classes
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
caps.latest.revision: 20
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 40d833772735e1079647f8f3205fb8db736843fd
ms.lasthandoff: 02/24/2017

---
# <a name="cdumpcontext-class"></a>CDumpContext 類別
支援使用人類看得懂的格式文字的資料流導向診斷輸出。  
  
## <a name="syntax"></a>語法  
  
```  
class CDumpContext  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CDumpContext::CDumpContext](#cdumpcontext)|建構 `CDumpContext` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CDumpContext::DumpAsHex](#dumpashex)|傾印以十六進位格式的指定項目。|  
|[CDumpContext::Flush](#flush)|排清的傾印內容緩衝區中的任何資料。|  
|[CDumpContext::GetDepth](#getdepth)|取得對應到傾印的深度的整數。|  
|[CDumpContext::HexDump](#hexdump)|傾印在十六進位格式的陣列中的位元組。|  
|[CDumpContext::SetDepth](#setdepth)|設定傾印的深度。|  
  
### <a name="public-operators"></a>公用運算子  
  
|名稱|說明|  
|----------|-----------------|  
|[CDumpContext::operator&lt;&lt;](#operator_lt_lt)|插入傾印內容的變數和物件。|  
  
## <a name="remarks"></a>備註  
 `CDumpContext`沒有基底類別。  
  
 您可以使用[afxDump](http://msdn.microsoft.com/library/4b3cfa3f-fb75-456a-9d99-a5601acbcb11)，預先宣告`CDumpContext`物件，來執行大部分的程式傾印。 `afxDump`物件是只能在 Mfc 程式庫的偵錯版本。  
  
 數個記憶體[診斷服務](../../mfc/reference/diagnostic-services.md)使用`afxDump`其輸出。  
  
 在 Windows 環境中，從預先定義之輸出`afxDump`物件，在概念上類似於`cerr`資料流，路由傳送至偵錯工具，透過 Windows 函式**OutputDebugString**。  
  
 `CDumpContext`類別具有多載的插入 ( ** << **) 運算子`CObject`傾印的物件資料的指標。 如果您需要自訂的傾印格式的衍生物件，覆寫[CObject::Dump](../../mfc/reference/cobject-class.md#dump)。 大部分的 Microsoft Foundation classes 會實作覆寫`Dump`成員函式。  
  
 不從衍生的類別`CObject`，例如`CString`， `CTime`，和`CTimeSpan`，有其自己的多載`CDumpContext`插入運算子，以執行常用的結構，例如**CFileStatus**， `CPoint`，和`CRect`。  
  
 如果您使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集的實作類別，然後在`CObject::Dump`會列印名稱您`CObject`-衍生的類別。 否則，它會列印`CObject`。  
  
 `CDumpContext`類別，就可以使用偵錯和發行版本的程式庫，但是`Dump`只在偵錯版本中定義成員函式。 使用**#ifdef _DEBUG**  /  `#endif`陳述式，以括號您的診斷程式碼，包括您的自訂`Dump`成員函式。  
  
 在建立您自己之前`CDumpContext`物件時，您必須建立`CFile`做為傾印目的地的物件。  
  
 如需有關`CDumpContext`，請參閱[偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。  
  
 **#define _DEBUG**  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `CDumpContext`  
  
## <a name="requirements"></a>需求  
 **標頭：** afx.h  
  
##  <a name="cdumpcontext"></a>CDumpContext::CDumpContext  
 建構類別的物件`CDumpContext`。  
  
```  
CDumpContext(CFile* pFile = NULL);
```  
  
### <a name="parameters"></a>參數  
 `pFile`  
 指標`CFile`傾印目的地的物件。  
  
### <a name="remarks"></a>備註  
 `afxDump`自動建構物件。  
  
 不會寫入至基礎`CFile`傾印內容是使用中; 否則會妨礙傾印。 在 Windows 環境中，輸出會路由傳送至偵錯工具，透過 Windows 函式**OutputDebugString**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&12;](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]  
  
##  <a name="dumpashex"></a>CDumpContext::DumpAsHex  
 傾印格式化為十六進位數字指定的型別。  
  
```  
CDumpContext& DumpAsHex(BYTE b);  
CDumpContext& DumpAsHex(DWORD dw);  
CDumpContext& DumpAsHex(int n);  
CDumpContext& DumpAsHex(LONG l);  
CDumpContext& DumpAsHex(LONGLONG n);  
CDumpContext& DumpAsHex(UINT u);  
CDumpContext& DumpAsHex(ULONGLONG n);  
CDumpContext& DumpAsHex(WORD w);
```  
  
### <a name="return-value"></a>傳回值  
 對 `CDumpContext` 物件的參考。  
  
### <a name="remarks"></a>備註  
 呼叫此成員函式傾印指定的型別，以十六進位數字的項目。 若要傾印陣列呼叫[CDumpContext::HexDump](#hexdump)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&13;](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]  
  
##  <a name="flush"></a>CDumpContext::Flush  
 強制執行任何剩餘的緩衝區寫入檔案中的資料附加至傾印內容。  
  
```  
void Flush();
```  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&14;](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]  
  
##  <a name="getdepth"></a>CDumpContext::GetDepth  
 判斷是否在處理序中深層或淺層傾印。  
  
```  
int GetDepth() const;  
```  
  
### <a name="return-value"></a>傳回值  
 所設定的傾印的深度`SetDepth`。  
  
### <a name="example"></a>範例  
  請參閱範例[SetDepth](#setdepth)。  
  
##  <a name="hexdump"></a>CDumpContext::HexDump  
 傾印格式化為十六進位數字的位元組的陣列。  
  
```  
void HexDump(
    LPCTSTR lpszLine,  
    BYTE* pby,  
    int nBytes,  
    int nWidth);
```  
  
### <a name="parameters"></a>參數  
 *lpszLine*  
 若要在新的一行開始輸出字串。  
  
 *pby*  
 緩衝區，其中包含要傾印的位元組指標。  
  
 `nBytes`  
 要傾印的位元組數目。  
  
 `nWidth`  
 每一行 （不輸出行的寬度），傾印的位元組數目上限。  
  
### <a name="remarks"></a>備註  
 若要將單一的特定項目類型以十六進位數字的傾印，呼叫[CDumpContext::DumpAsHex](#dumpashex)。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&15;](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]  
  
##  <a name="operator_lt_lt"></a>CDumpContext::operator&lt;&lt;  
 輸出指定要傾印內容的資料。  
  
```  
CDumpContext& operator<<(const CObject* pOb);  
CDumpContext& operator<<(const CObject& ob);  
CDumpContext& operator<<(LPCTSTR lpsz);  
CDumpContext& operator<<(const void* lp);  
CDumpContext& operator<<(BYTE by);  
CDumpContext& operator<<(WORD w);  
CDumpContext& operator<<(DWORD dw);  
CDumpContext& operator<<(int n);  
CDumpContext& operator<<(double d);  
CDumpContext& operator<<(float f);  
CDumpContext& operator<<(LONG l);  
CDumpContext& operator<<(UINT u);  
CDumpContext& operator<<(LPCWSTR lpsz);  
CDumpContext& operator<<(LPCSTR lpsz);  
CDumpContext& operator<<(LONGLONG n);  
CDumpContext& operator<<(ULONGLONG n);  
CDumpContext& operator<<(HWND h);  
CDumpContext& operator<<(HDC h);  
CDumpContext& operator<<(HMENU h);  
CDumpContext& operator<<(HACCEL h);  
CDumpContext& operator<<(HFONT h);
```  
  
### <a name="return-value"></a>傳回值  
 A`CDumpContext`參考。 使用傳回值，您可以撰寫多個插入一行的原始程式碼。  
  
### <a name="remarks"></a>備註  
 插入運算子多載的`CObject`指標以及大多數的基本型別。 字元指標會產生傾印的字串內容。指標`void`導致只有位址的十六進位傾印。 A **LONGLONG**產生傾印的 64 位元帶正負號的整數。A **ULONGLONG**產生傾印的 64 位元不帶正負號的整數。  
  
 如果您使用`IMPLEMENT_DYNAMIC`或`IMPLEMENT_SERIAL`巨集，您的類別，然後插入運算子的實作中透過`CObject::Dump`，會列印名稱您`CObject`-衍生的類別。 否則，它會列印`CObject`。 如果您覆寫`Dump`函式類別，則您可以提供更有意義的物件內容，而不是十六進位傾印的輸出。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&17;](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]  
  
##  <a name="setdepth"></a>CDumpContext::SetDepth  
 設定傾印的深度。  
  
```  
void SetDepth(int nNewDepth);
```  
  
### <a name="parameters"></a>參數  
 *nNewDepth*  
 新的深度值。  
  
### <a name="remarks"></a>備註  
 如果您基本型別或簡單傾印`CObject`，其中包含其他物件，沒有指標，則值為 0 就已足夠。 值大於 0 指定的所有物件的深層傾印傾印以遞迴方式。 例如，集合的深層傾印會傾印集合的所有項目。 在衍生類別中，您可以使用其他特定深度的值。  
  
> [!NOTE]
>  深層傾印中未偵測到循環參考，而且可能會導致無限迴圈。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_Utilities #&16;](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CFile 類別](../../mfc/reference/cfile-class.md)   
 [CObject 類別](../../mfc/reference/cobject-class.md)


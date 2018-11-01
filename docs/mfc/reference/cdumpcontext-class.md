---
title: CDumpContext 類別
ms.date: 11/04/2016
f1_keywords:
- CDumpContext
- AFX/CDumpContext
- AFX/CDumpContext::CDumpContext
- AFX/CDumpContext::DumpAsHex
- AFX/CDumpContext::Flush
- AFX/CDumpContext::GetDepth
- AFX/CDumpContext::HexDump
- AFX/CDumpContext::SetDepth
helpviewer_keywords:
- CDumpContext [MFC], CDumpContext
- CDumpContext [MFC], DumpAsHex
- CDumpContext [MFC], Flush
- CDumpContext [MFC], GetDepth
- CDumpContext [MFC], HexDump
- CDumpContext [MFC], SetDepth
ms.assetid: 98c52b2d-14b5-48ed-b423-479a4d1c60fa
ms.openlocfilehash: 391804d05800e3979add7bee6342308de4253602
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668815"
---
# <a name="cdumpcontext-class"></a>CDumpContext 類別

支援使用人類看得懂的格式文字的資料流導向診斷輸出。

## <a name="syntax"></a>語法

```
class CDumpContext
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CDumpContext::CDumpContext](#cdumpcontext)|建構 `CDumpContext` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CDumpContext::DumpAsHex](#dumpashex)|傾印以十六進位格式的指定項目。|
|[CDumpContext::Flush](#flush)|排清的傾印內容緩衝區中的任何資料。|
|[CDumpContext::GetDepth](#getdepth)|取得對應至傾印的深度的整數。|
|[CDumpContext::HexDump](#hexdump)|傾印以十六進位格式將陣列中包含的位元組。|
|[CDumpContext::SetDepth](#setdepth)|設定傾印的深度。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CDumpContext::operator &lt;&lt;](#operator_lt_lt)|插入傾印內容的變數和物件。|

## <a name="remarks"></a>備註

`CDumpContext` 沒有基底類別。

您可以使用[afxDump](diagnostic-services.md#afxdump)，預先宣告`CDumpContext`物件，大部分您傾印。 `afxDump`物件是只能在 Microsoft Foundation 類別庫的偵錯版本。

數個記憶體[診斷服務](../../mfc/reference/diagnostic-services.md)使用`afxDump`其輸出。

在 Windows 環境中，從預先定義的輸出`afxDump`物件，在概念上類似於`cerr`串流，會路由傳送至偵錯工具，透過 Windows 函式`OutputDebugString`。

`CDumpContext`類別具有多載的插入 ( **<<**) 運算子`CObject`傾印物件的資料的指標。 如果您需要自訂的傾印格式的衍生物件時，會覆寫[CObject::Dump](../../mfc/reference/cobject-class.md#dump)。 大部分的 Microsoft Foundation classes 會實作覆寫`Dump`成員函式。

不從衍生的類別`CObject`，這類`CString`， `CTime`，以及`CTimeSpan`，有自己的多載`CDumpContext`插入運算子，為執行常用的結構，例如`CFileStatus`， `CPoint`，和`CRect`.

如果您使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或是[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)巨集的實作中您的類別，然後`CObject::Dump`會列印名稱您`CObject`-衍生的類別。 否則，它只會列印`CObject`。

`CDumpContext`類別可用於偵錯和發行版本的程式庫，但`Dump`成員函式只會定義在偵錯版本。 使用 **#ifdef _DEBUG**  /  `#endif`陳述式來括住您的診斷程式碼，包括您的自訂`Dump`成員函式。

在您建立您自己之前`CDumpContext`物件，您必須建立`CFile`物件做為傾印目的地。

如需詳細資訊`CDumpContext`，請參閱 <<c2> [ 偵錯 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>繼承階層

`CDumpContext`

## <a name="requirements"></a>需求

**標頭：** afx.h

##  <a name="cdumpcontext"></a>  CDumpContext::CDumpContext

建構的物件類別`CDumpContext`。

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>參數

*pFile*<br/>
指標`CFile`傾印目的地的物件。

### <a name="remarks"></a>備註

`afxDump`自動建構物件。

不要寫入至基礎`CFile`傾印內容是使用中; 否則您會干擾傾印。 在 Windows 環境中，輸出會路由傳送至偵錯工具，透過 Windows 函式`OutputDebugString`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

##  <a name="dumpashex"></a>  CDumpContext::DumpAsHex

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

呼叫此成員函式以傾印指定的型別為十六進位的數字的項目。 若要傾印陣列，呼叫[CDumpContext::HexDump](#hexdump)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

##  <a name="flush"></a>  CDumpContext::Flush

強制執行任何剩餘的緩衝區寫入檔案中的資料附加至傾印內容。

```
void Flush();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

##  <a name="getdepth"></a>  CDumpContext::GetDepth

判斷是否在程序中的深層或淺層傾印。

```
int GetDepth() const;
```

### <a name="return-value"></a>傳回值

所設定的傾印的深度`SetDepth`。

### <a name="example"></a>範例

  範例，請參閱[SetDepth](#setdepth)。

##  <a name="hexdump"></a>  CDumpContext::HexDump

傾印格式化為十六進位數字的位元組陣列。

```
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>參數

*lpszLine*<br/>
要輸出的新行開頭的字串。

*pby*<br/>
包含要傾印的位元組之緩衝區的指標。

*nBytes*<br/>
要傾印的位元組數目。

*nWidth*<br/>
每一行 （無法輸出行寬度），傾印的位元組數目上限。

### <a name="remarks"></a>備註

若要傾印的十六進位數字的單一特定項目類型，呼叫[CDumpContext::DumpAsHex](#dumpashex)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

##  <a name="operator_lt_lt"></a>  CDumpContext::operator &lt;&lt;

將輸出傾印內容至指定的資料。

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

A`CDumpContext`參考。 使用傳回的值，您可以在單一原始程式碼行上撰寫多個插入。

### <a name="remarks"></a>備註

針對多載插入運算子`CObject`指標以及大多數的基本型別。 字元的指標會產生的字串內容; 傾印。指標**void**導致只有位址的十六進位傾印。 LONGLONG 產生在 64 位元帶正負號的整數; 傾印ULONGLONG 產生的傾印的 64 位元不帶正負號的整數。

如果您使用您的類別或 IMPLEMENT_SERIAL 巨集，在您的類別，然後插入運算子的實作中透過`CObject::Dump`，將會列印名稱您`CObject`-衍生的類別。 否則，它只會列印`CObject`。 如果您覆寫`Dump`函式的類別，則您可以提供之物件的內容，而不是十六進位傾印更有意義的輸出。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

##  <a name="setdepth"></a>  CDumpContext::SetDepth

設定傾印的深度。

```
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>參數

*nNewDepth*<br/>
新的深度值。

### <a name="remarks"></a>備註

如果您傾印的基本型別或簡單`CObject`，未不包含任何其他物件的指標，則值為 0 就已足夠。 值大於 0 指定所在的所有物件的深層傾印傾印以遞迴方式。 比方說，集合的深層傾印會傾印集合的所有項目。 在衍生類別中，您可以使用其他特定的深度值。

> [!NOTE]
>  深入的傾印中未偵測到循環參考，而且可能會導致無限迴圈。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)

---
title: CDumpCoNtext 類別
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
ms.openlocfilehash: 3a81e06586e6de14d57ce4c4de36dc30c73383f1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212510"
---
# <a name="cdumpcontext-class"></a>CDumpCoNtext 類別

支援使用人類看得懂的格式文字的資料流導向診斷輸出。

## <a name="syntax"></a>語法

```
class CDumpContext
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CDumpCoNtext：： CDumpCoNtext](#cdumpcontext)|建構 `CDumpContext` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CDumpCoNtext：:D umpAsHex](#dumpashex)|以十六進位格式傾印指定的專案。|
|[CDumpCoNtext：： Flush](#flush)|排清傾印內容緩衝區中的任何資料。|
|[CDumpCoNtext：： GetDepth](#getdepth)|取得對應到傾印深度的整數。|
|[CDumpCoNtext：： HexDump](#hexdump)|以十六進位格式傾印陣列中包含的位元組。|
|[CDumpCoNtext：： SetDepth](#setdepth)|設定傾印的深度。|

### <a name="public-operators"></a>公用運算子

|名稱|說明|
|----------|-----------------|
|[CDumpCoNtext：： operator&lt;&lt;](#operator_lt_lt)|將變數和物件插入傾印內容中。|

## <a name="remarks"></a>備註

`CDumpContext`沒有基類。

您可以使用[afxDump](diagnostic-services.md#afxdump)（預先宣告 `CDumpContext` 物件）來進行大部分的傾印。 `afxDump`物件只能在 MFC 程式庫的 Debug 版本中使用。

幾個記憶體[診斷服務](../../mfc/reference/diagnostic-services.md)用於 `afxDump` 輸出。

在 Windows 環境下，預先定義的 `afxDump` 物件（概念上類似資料流程）的輸出會透過 Windows 函式 `cerr` 路由傳送至偵錯工具 `OutputDebugString` 。

針對傾印 `CDumpContext` 物件資料的指標，此類別具有多載插入（ **<<** ）運算子 `CObject` 。 如果您需要衍生物件的自訂傾印格式，請覆寫[CObject：:D ump](../../mfc/reference/cobject-class.md#dump)。 大部分的 Microsoft Foundation 類別都會執行覆寫的成員函式 `Dump` 。

不是衍生自的類別（ `CObject` 例如 `CString` 、 `CTime` 和）有自己的多載 `CTimeSpan` `CDumpContext` 插入運算子，如同經常使用的結構，例如 `CFileStatus` 、 `CPoint` 和 `CRect` 。

如果您在類別的執行中使用[IMPLEMENT_DYNAMIC](../../mfc/reference/run-time-object-model-services.md#implement_dynamic)或[IMPLEMENT_SERIAL](../../mfc/reference/run-time-object-model-services.md#implement_serial)宏，則 `CObject::Dump` 會列印 `CObject` 衍生類別的名稱。 否則，它會列印 `CObject` 。

`CDumpContext`類別可用於程式庫的 debug 和 Release 版本，但成員函式 `Dump` 只會在 debug 版本中定義。 使用 **#ifdef _DEBUG**  /  `#endif` 語句來括住您的診斷程式代碼，包括您的自訂成員函式 `Dump` 。

建立自己的物件之前 `CDumpContext` ，您必須先建立一個 `CFile` 做為傾印目的地的物件。

如需的詳細資訊 `CDumpContext` ，請參閱[調試 MFC 應用程式](/visualstudio/debugger/mfc-debugging-techniques)。

**#define _DEBUG**

## <a name="inheritance-hierarchy"></a>繼承階層架構

`CDumpContext`

## <a name="requirements"></a>需求

**標頭：** afx。h

## <a name="cdumpcontextcdumpcontext"></a><a name="cdumpcontext"></a>CDumpCoNtext：： CDumpCoNtext

構造類別的物件 `CDumpContext` 。

```
CDumpContext(CFile* pFile = NULL);
```

### <a name="parameters"></a>參數

*pFile*<br/>
物件的指標， `CFile` 這是傾印目的地。

### <a name="remarks"></a>備註

`afxDump`系統會自動建造物件。

當傾印 `CFile` 內容為作用中時，請勿寫入基礎，否則會干擾傾印。 在 Windows 環境下，輸出會透過 Windows 函數路由傳送至偵錯工具 `OutputDebugString` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#12](../../mfc/codesnippet/cpp/cdumpcontext-class_1.cpp)]

## <a name="cdumpcontextdumpashex"></a><a name="dumpashex"></a>CDumpCoNtext：:D umpAsHex

傾印指定的類型，並將其格式化為十六進位數位。

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

`CDumpContext` 物件的參考。

### <a name="remarks"></a>備註

呼叫這個成員函式，將指定類型的專案傾印為十六進位數位。 若要傾印陣列，請呼叫[CDumpCoNtext：： HexDump](#hexdump)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#13](../../mfc/codesnippet/cpp/cdumpcontext-class_2.cpp)]

## <a name="cdumpcontextflush"></a><a name="flush"></a>CDumpCoNtext：： Flush

強制將緩衝區中剩餘的任何資料寫入附加至傾印內容的檔案。

```cpp
void Flush();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#14](../../mfc/codesnippet/cpp/cdumpcontext-class_3.cpp)]

## <a name="cdumpcontextgetdepth"></a><a name="getdepth"></a>CDumpCoNtext：： GetDepth

判斷深層或淺層傾印是否正在處理中。

```
int GetDepth() const;
```

### <a name="return-value"></a>傳回值

所設定之傾印的深度 `SetDepth` 。

### <a name="example"></a>範例

  請參閱[SetDepth](#setdepth)的範例。

## <a name="cdumpcontexthexdump"></a><a name="hexdump"></a>CDumpCoNtext：： HexDump

傾印格式化為十六進位數位的位元組陣列。

```cpp
void HexDump(
    LPCTSTR lpszLine,
    BYTE* pby,
    int nBytes,
    int nWidth);
```

### <a name="parameters"></a>參數

*lpszLine*<br/>
要在新行開頭輸出的字串。

*pby*<br/>
包含要傾印之位元組的緩衝區指標。

*nBytes*<br/>
要傾印的位元組數。

*nWidth*<br/>
每一行傾印的最大位元組數（不是輸出行的寬度）。

### <a name="remarks"></a>備註

若要將單一特定的專案類型傾印成十六進位數位，請呼叫[CDumpCoNtext：:D umpashex](#dumpashex)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#15](../../mfc/codesnippet/cpp/cdumpcontext-class_4.cpp)]

## <a name="cdumpcontextoperator-ltlt"></a><a name="operator_lt_lt"></a>CDumpCoNtext：： operator&lt;&lt;

將指定的資料輸出到傾印內容。

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

`CDumpContext` 參考。 使用傳回值，您可以在一行原始程式碼上撰寫多個插入。

### <a name="remarks"></a>備註

插入運算子會針對指標和 `CObject` 大部分的基本型別進行多載。 字元的指標會產生字串內容的傾印;的指標 **`void`** 只會產生位址的十六進位傾印。 LONGLONG 會產生64位帶正負號整數的傾印;ULONGLONG 會產生64位不帶正負號整數的傾印。

如果您在類別的執行中使用 IMPLEMENT_DYNAMIC 或 IMPLEMENT_SERIAL 宏，則插入運算子 `CObject::Dump` 將會列印 `CObject` 衍生類別的名稱。 否則，它會列印 `CObject` 。 如果您覆寫類別的函式 `Dump` ，則可以提供更有意義的物件內容輸出，而不是十六進位傾印。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#17](../../mfc/codesnippet/cpp/cdumpcontext-class_5.cpp)]

## <a name="cdumpcontextsetdepth"></a><a name="setdepth"></a>CDumpCoNtext：： SetDepth

設定傾印的深度。

```cpp
void SetDepth(int nNewDepth);
```

### <a name="parameters"></a>參數

*nNewDepth*<br/>
新的深度值。

### <a name="remarks"></a>備註

如果您要傾印基本型別，或不 `CObject` 包含其他物件指標的簡單型別，則值為0就已足夠。 大於0的值會指定深度傾印，其中所有物件會以遞迴方式傾印。 例如，集合的深層傾印會傾印集合的所有元素。 您可以在衍生類別中使用其他特定的深度值。

> [!NOTE]
> 在深層傾印中不會偵測到迴圈參考，而且可能會導致無限迴圈。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#16](../../mfc/codesnippet/cpp/cdumpcontext-class_6.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CFile 類別](../../mfc/reference/cfile-class.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)

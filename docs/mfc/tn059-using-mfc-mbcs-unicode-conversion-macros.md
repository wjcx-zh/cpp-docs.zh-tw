---
title: TN059:使用 MFC Mbcs-unicode 轉換巨集
ms.date: 11/04/2016
helpviewer_keywords:
- MFCANS32.DLL
- Unicode [MFC], conversion macros
- Unicode [MFC], OLE interfaces
- conversion macros [MFC]
- converting Unicode
- MBCS [MFC], conversion macros
- macros [MFC], MBCS conversion macros
- TN059
ms.assetid: a2aab748-94d0-4e2f-8447-3bd07112a705
ms.openlocfilehash: 6c182ff584404fb91de8ff5e8020ec2e6ef9f950
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611853"
---
# <a name="tn059-using-mfc-mbcsunicode-conversion-macros"></a>TN059:使用 MFC MBCS/Unicode 轉換巨集

> [!NOTE]
>  下列技術提示自其納入線上文件以來，未曾更新。 因此，有些程序和主題可能已過期或不正確。 如需最新資訊，建議您在線上文件索引中搜尋相關的主題。

此提示描述如何使用 MBCS/Unicode 轉換的巨集 (在 AFXPRIV.H 中定義)。 如果您的應用程式會直接處理 OLE API，或基於某些原因，常常需要在 Unicode 和 MBCS 之間進行轉換，則使用這些巨集是最有用的。

## <a name="overview"></a>總覽

在 MFC 3.x 中，當呼叫 OLE 介面時，會使用一個特別的 DLL (MFCANS32.DLL) 自動在 Unicode 和 MBCS 之間進行轉換。 這個 DLL 是一個幾乎透明的層級，允許撰寫 OLE API 和介面為 MBCS 的 OLE 應用程式，即使它們永遠都是 Unicode (除了 Macintosh 之外)。 雖然這個層級很方便且可讓應用程式從 Win16 快速移植到 Win32 (MFC、Microsoft Word、Microsoft Excel 和 VBA 是使用這項技術的一些 Microsoft 應用程式)，但它有時會影響效能。 因此，MFC 4.x 不會使用這個 DLL，而是直接與 Unicode OLE 介面溝通。 為了要這麼做，MFC 需要在呼叫 OLE 介面時從 Unicode 轉換成 MBCS，而且在實作 OLE 介面時通常需要從 Unicode 轉換為 MBCS。 為了方便且有效地處理這種情形，其建立了一些巨集以使這項轉換更加容易。

建立這類巨集的其中一項最大的阻礙是記憶體配置。 由於字串無法立即轉換，必須配置新記憶體以保留轉換結果。 這可以使用下列程式碼達成類似的功能：

```
// we want to convert an MBCS string in lpszA
int nLen = MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    NULL,
    NULL);

LPWSTR lpszW = new WCHAR[nLen];
MultiByteToWideChar(CP_ACP,
    0,
    lpszA, -1,
    lpszW,
    nLen);

// use it to call OLE here
pI->SomeFunctionThatNeedsUnicode(lpszW);

// free the string
delete[] lpszW;
```

這個方法產生了一些問題。 主要的問題是需要撰寫、測試及偵錯大量的程式碼。 以前只是簡單的函式呼叫，現在變得較為複雜。 此外，這樣做會造成執行階段的重大額外負荷。 每次完成轉換，就必須配置和釋放記憶體堆積。 最後，上述程式碼需要為了 Unicode 和 Macintosh 組建 (不需要進行這項轉換) 加入適當的 `#ifdefs`。

所提供的解決方案為建立一些巨集，其中 1) 使用遮罩區分各種平台之間的差異 2) 使用一種有效的記憶體配置方案，以及 3) 可以簡單地插入現有的原始程式碼。 以下其中一種定義的範例：

```
#define A2W(lpa) (\
((LPCSTR)lpa == NULL) NULL : (\
    _convert = (strnlen(lpa)+1),\
    AfxA2WHelper((LPWSTR) alloca(_convert*2),
    lpa,
    _convert)\)\)
```

使用這個巨集而不是上述程式碼讓事情簡單化：

```
// use it to call OLE here
USES_CONVERSION;
pI->SomeFunctionThatNeedsUnicode(T2OLE(lpszA));
```

其中會因轉換而需要進行額外的呼叫，不過，使用巨集是簡單且有效的。

每一個巨集的實作會使用 _alloca() 函式從堆疊中 (而不是堆積) 配置記憶體。 從堆疊配置記憶體會比在堆積上配置記憶體更加快速，而且會在函式結束時自動釋放記憶體。 此外，巨集會避免呼叫`MultiByteToWideChar`(或`WideCharToMultiByte`) 一次以上。 這是藉由配置比所需更多的記憶體來完成。 我們知道 MBC 會轉換成最多一個**WCHAR**而針對每個**WCHAR**我們有兩個 MBC 位元組最大值。 藉由配置比所需多一點，但一定足夠用於處理轉換第二次呼叫的記憶體，可避免第二次呼叫轉換函式。 Helper 函式呼叫`AfxA2Whelper`可減少必須完成才能執行轉換的引數推播數目 (這會導致較小的程式碼，比如果呼叫`MultiByteToWideChar`直接)。

為了要讓巨集具有儲存暫存長度的空間，您必須在每個使用轉換巨集的函式中宣告名為 _convert 的區域變數。 這是藉由叫用 USES_CONVERSION 巨集，在範例中，如上所示。

其中提供泛型轉換巨集和 OLE 專屬巨集。 這兩個不同的巨集將於下方討論。 所有巨集皆位於 AFXPRIV.H 在。

## <a name="generic-conversion-macros"></a>泛型轉換巨集

泛型轉換巨集會形成基礎機制。 先前章節中的巨集範例和實作 (A2W) 就是這一類的「泛型」巨集。 它不會特別與 OLE 相關。 以下列出一組泛型巨集：

```
A2CW      (LPCSTR) -> (LPCWSTR)
A2W      (LPCSTR) -> (LPWSTR)
W2CA      (LPCWSTR) -> (LPCSTR)
W2A      (LPCWSTR) -> (LPSTR)
```

除了轉換文字以外，也有巨集和 Helper 函式可轉換 `TEXTMETRIC`、`DEVMODE`、`BSTR` 和 OLE 配置的字串。 這些巨集已超出本文的討論範圍-AFXPRIV 參考。如需有關這些巨集 H。

## <a name="ole-conversion-macros"></a>OLE 轉換巨集

OLE 轉換巨集特別設計來處理預期的函式**OLESTR**字元。 如果檢查 OLE 標頭，您會看到許多參照**LPCOLESTR**並**OLECHAR**。 這些類型用來以非專屬於平台的方法參考 OLE 介面中使用的字元類型。 **OLECHAR**對應至**char** Win16 和 Macintosh 平台並**WCHAR**在 Win32 中。

若要保留的數目 **#ifdef**最少的程式碼在 MFC 中的指示詞有類似的巨集，針對每個轉換的 OLE 字串所涵蓋的其中。 以下巨集最為常用：

```
T2COLE   (LPCTSTR) -> (LPCOLESTR)
T2OLE   (LPCTSTR) -> (LPOLESTR)
OLE2CT   (LPCOLESTR) -> (LPCTSTR)
OLE2T   (LPCOLESTR) -> (LPCSTR)
```

同樣地，有執行 TEXTMETRIC、 DEVMODE、 BSTR、 和 OLE 配置字串相似的巨集。 如需詳細資訊，請參閱 AFXPRIV.H。

## <a name="other-considerations"></a>其他考量

不要在緊密迴圈中使用巨集。 例如，不要撰寫以下類型的程式碼：

```
void BadIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, T2COLE(lpsz));

}
```

上述程式碼可能會根據字串 `lpsz` 的內容造成在堆疊上配置數 MB 的記憶體！ 這也需要時間轉換迴圈中每個反覆項目的字串。 相反地，請將這類常數轉換移至迴圈外：

```
void MuchBetterIterateCode(LPCTSTR lpsz)
{
    USES_CONVERSION;
    LPCOLESTR lpszT = T2COLE(lpsz);

    for (int ii = 0; ii <10000; ii++)
    pI->SomeMethod(ii, lpszT);

}
```

如果字串不是常數，則請在函式中封裝呼叫的方法。 這將允許每一次都釋放轉換緩衝區。 例如：

```
void CallSomeMethod(int ii, LPCTSTR lpsz)
{
    USES_CONVERSION;
    pI->SomeMethod(ii, T2COLE(lpsz));

}

void MuchBetterIterateCode2(LPCTSTR* lpszArray)
{
    for (int ii = 0; ii <10000; ii++)
    CallSomeMethod(ii, lpszArray[ii]);

}
```

不要傳回其中一個巨集的結果，除非傳回值意味著會在傳回之前建立資料的複本。 例如，以下這個程式碼是不好的：

```
LPTSTR BadConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // bad! returning alloca memory
}
```

上述程式碼可以藉由將傳回值變更為複製的值以進行修正：

```
CString BetterConvert(ISomeInterface* pI)
{
    USES_CONVERSION;
    LPOLESTR lpsz = NULL;
    pI->GetFileName(&lpsz);

LPTSTR lpszT = OLE2T(lpsz);

    CoMemFree(lpsz);

return lpszT; // CString makes copy
}
```

巨集容易使用且容易插入至程式碼，但是您必須在使用它們時特別注意上述的各種警告。

## <a name="see-also"></a>另請參閱

[依編號顯示的技術提示](../mfc/technical-notes-by-number.md)<br/>
[依分類區分的技術提示](../mfc/technical-notes-by-category.md)

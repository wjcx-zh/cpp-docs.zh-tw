---
title: 交互匯入
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: 38f2e08139566ce6c70755cd367edf93677ef9af
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614405"
---
# <a name="mutual-imports"></a>交互匯入

匯出或匯入到另一個可執行檔的檔案提供很複雜的情況，當匯入相互 （或循環）。 比方說，這兩個 Dll 從匯入符號彼此相互遞迴函式類似。

相互匯入的可執行檔 (通常是 Dll) 的問題在於，兩者可以建置但不建置其他第一個。 每個建置流程所需，做為輸入，其他組建程序所產生的匯入程式庫。

解決方案是使用程式庫公用程式使用 /DEF 選項時，這會產生匯入程式庫，而不需建置可執行檔。 使用此公用程式，您可以建立您所需的所有匯入程式庫不管涉及多少的 Dll 或相依性有多複雜。

處理交互匯入一般的解決方法是：

1. 接著需要每個 DLL。 （任何順序是可行的的雖然有些順序會更接近最佳函式）。如果所有必要的匯入程式庫會存在，而且是最新狀態，執行來建置可執行檔 (DLL) 的連結。 這會產生匯入程式庫。 否則，請執行 LIB 產生匯入程式庫。

   執行 LIB /DEF 選項會產生其他檔案。EXP 延伸模組。 。EXP 檔案必須稍後用來建置可執行檔。

1. 之後使用連結或程式庫來建置所有匯入程式庫，請返回並執行建置在上一個步驟中未建立任何可執行檔的連結。 請注意，必須連結列上指定對應的.exp 檔案。

   如果您有執行 LIB 公用程式在稍早針對 DLL1 產生匯入程式庫，LIB 會產生檔 DLL1.exp 以及。 建置 DLL1.dlll 時，您必須使用 DLL1.exp 做為連結的輸入。

下圖會顯示兩個相互匯入 Dll、 DLL1 和 DLL2 的解決方案。 /DEF 選項的設定，在 DLL1 執行 LIB，為步驟 1。 步驟 1 產生 DLL1.lib、 匯入程式庫和 DLL1.exp。在步驟 2 中，匯入程式庫來建置 DLL2，接著會產生的匯入程式庫，為 DLL2 的符號。 步驟 3 建立 DLL1，利用 DLL1.exp 和 DLL2.lib 做為輸入。 請注意 DLL2.exp 檔不需要，因為程式庫不用來建置 DLL2 的匯入程式庫。

![使用交互匯入連結的兩個 Dll](../build/media/vc37yj1.gif "使用交互匯入連結的兩個 Dll")<br/>
交互匯入與連結的兩個 Dll

## <a name="limitations-of-afxext"></a>_AFXEXT 的限制

您可以使用`_AFXEXT`MFC 延伸模組 Dll 只要您不需要多個圖層的 MFC 擴充 Dll 的前置處理器符號。 如果您有 MFC 擴充 Dll 呼叫，或衍生自類別，在您自己的 MFC 擴充 Dll，然後從 MFC 類別衍生，您必須使用您自己的前置處理器符號，以避免模稜兩可。

問題是，在 Win32 中，您必須明確宣告為任何資料 **__declspec （dllexport)** 如果要匯出從 DLL，並 **__declspec （dllimport)** 它是否要從 DLL 匯入。 當您定義`_AFXEXT`，MFC 標頭，確定**AFX_EXT_CLASS**正確定義。

當您擁有多個圖層，一個符號這類**AFX_EXT_CLASS**是不夠的因為 MFC 擴充 DLL 可能會匯出新的類別，以及從另一個 MFC 擴充 DLL 匯入其他類別。 若要解決此問題，請使用特殊的前置處理器符號，指出您要建置 DLL 本身而非使用 DLL。 例如，假設兩個 MFC 擴充 Dll，A.dll 和 B.dll。 每個分別匯出 A.h 和 B.h 中的某些類別。 B.dll 使用 A.dll 的類別。 標頭檔看起來像這樣：

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

建置 A.dll 時，它以`/D A_IMPL`而且 B.dll 建置時，它會根據`/D B_IMPL`。 每個 dll，請使用不同的符號`CExampleB`匯出和`CExampleA`建置 B.dll 時匯入。 `CExampleA` 為匯出時建置 A.dll 和 B.dll （或是某些其他用戶端） 使用時，匯入。

使用內建時，就無法執行這種分層**AFX_EXT_CLASS**和`_AFXEXT`前置處理器符號。 上面所述的技巧可解決此問題的方式沒有不同於建置其作用中的技術、 資料庫和網路 MFC 擴充 Dll 時，會使用 MFC 本身的機制。

## <a name="not-exporting-the-entire-class"></a>不會匯出整個類別

當您不匯出整個類別時，您必須確定建立的 MFC 巨集的必要資料項目都正確匯出。 這可以藉由重新定義`AFX_DATA`特定類別的巨集。 這應該不會匯出整個類別的任何時間。

例如: 

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>請您指定選項。

- [從 DLL 匯出](../build/exporting-from-a-dll.md)

- [匯出從 DLL 使用。DEF 檔](../build/exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)

- [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)

- [將應用程式使用 __declspec （dllimport） 匯入](../build/importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [LIB 公共事業和 /DEF 選項](../build/reference/lib-reference.md)

## <a name="see-also"></a>另請參閱

[匯入和匯出](../build/importing-and-exporting.md)
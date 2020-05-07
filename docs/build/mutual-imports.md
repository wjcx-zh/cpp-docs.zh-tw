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
ms.openlocfilehash: f01e69138a6ca1744645a1c2fa8525b7088e260d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295665"
---
# <a name="mutual-imports"></a>交互匯入

當匯入為相互（或迴圈）時，匯出或匯入至另一個可執行檔會帶來複雜的複雜性。 例如，兩個 Dll 會從彼此匯入符號，類似于相互遞迴函式。

相互匯入可執行檔（通常是 Dll）的問題是，不需要建立另一個檔案就可以建立。 每個組建程式都需要做為輸入，另一個組建進程所產生的匯入程式庫。

解決方法是使用 LIB 公用程式搭配/DEF 選項，它會產生匯入程式庫，而不會建立可執行檔。 您可以使用這個公用程式來建立所需的所有匯入程式庫，不論有多少 Dll 或相依性有多複雜。

處理相互匯入的一般解決方案是：

1. 輪流採用每個 DLL。 （所有訂單都是可行的，雖然有些訂單較最佳。）如果所有需要的匯入程式庫都存在，而且是最新的，請執行 LINK 來建立可執行檔（DLL）。 這會產生匯入程式庫。 否則，請執行 LIB 以產生匯入程式庫。

   使用/DEF 選項執行 LIB 會產生具有的其他檔案。EXP 延伸模組。 該.稍後必須使用 EXP 檔案來建立可執行檔。

1. 使用 LINK 或 LIB 建立所有匯入程式庫之後，請返回並執行連結，以建立在上一個步驟中未建立的任何可執行檔。 請注意，您必須在連結行上指定對應的 .exp 檔案。

   如果您先前已執行過 LIB 公用程式來產生 DLL1 的匯入程式庫，則 LIB 也會產生檔案 DLL1。 建立 DLL1 時，您必須使用 DLL1 做為連結的輸入。

下圖顯示兩個相互匯入 Dll （DLL1 和 DLL2）的解決方案。 步驟1是在 DLL1 上執行 LIB，並設定/DEF 選項。 步驟1會產生 DLL1、匯入程式庫和 DLL1。在步驟2中，會使用匯入程式庫來建立 DLL2，進而產生 DLL2's 符號的匯入程式庫。 步驟3建立 DLL1，方法是使用 DLL1 和 DLL2 做為輸入。 請注意，DLL2 的 .exp 檔案不是必要的，因為 LIB 並未用來建立 DLL2's 匯入程式庫。

![使用相互匯入連結兩個 dll](media/vc37yj1.gif "使用相互匯入連結兩個 dll")<br/>
使用相互匯入連結兩個 Dll

## <a name="limitations-of-_afxext"></a>_AFXEXT 的限制

您可以使用 MFC `_AFXEXT`延伸模組 dll 的預處理器符號，前提是您沒有 mfc 延伸模組 dll 的多個層級。 如果您的 MFC 延伸 Dll 會呼叫或衍生自您自己的 MFC 擴充 Dll 中的類別，然後再衍生自 MFC 類別，則您必須使用自己的預處理器符號來避免不明確。

問題在於，在 Win32 中，如果要從 DLL 匯出，您必須將任何資料明確宣告為 **__declspec （dllexport）** ，如果要從 dll 匯入，則 **__declspec （dllimport）** 。 當您定義`_AFXEXT`時，MFC 標頭會確保已正確定義**AFX_EXT_CLASS** 。

當您有多個層級時，一個符號（例如**AFX_EXT_CLASS** ）並不夠，因為 MFC 延伸 dll 可能會匯出新的類別，以及從另一個 MFC 延伸 dll 匯入其他類別。 若要解決這個問題，請使用特殊的預處理器符號，表示您要建立 DLL 本身，而不是使用 DLL。 例如，假設有兩個 MFC 延伸 Dll： .dll 和 b. .dll。 它們會分別匯出. h 和 b. h 中的一些類別。 B. 使用 .dll 的類別。 標頭檔看起來會像這樣：

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

建立 .dll 後，它是以`/D A_IMPL`建立的，而建立了 B. dll 時，則是以`/D B_IMPL`建立。 針對每個 DLL 使用個別的符號`CExampleB` ，會匯出`CExampleA` ，並在建立 b. 時匯入。 `CExampleA`會在建立 .dll 時匯出，並在由 B .dll （或其他用戶端）使用時匯入。

使用內建的**AFX_EXT_CLASS**和`_AFXEXT`預處理器符號時，無法完成這種類型的分層。 上述技術可解決這個問題，方法與建立其作用中技術、資料庫和網路 MFC 延伸 Dll 時，MFC 本身所使用的機制不同。

## <a name="not-exporting-the-entire-class"></a>不匯出整個類別

當您未匯出整個類別時，您必須確定已正確匯出 MFC 宏所建立的必要資料項目。 這可以藉由重新定義`AFX_DATA`為特定類別的宏來完成。 當您不想要匯出整個類別時，應該執行此動作。

例如：

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

### <a name="what-do-you-want-to-do"></a>您想要做什麼事？

- [從 DLL 匯出](exporting-from-a-dll.md)

- [使用從 DLL 匯出。DEF 檔案](exporting-from-a-dll-using-def-files.md)

- [使用 __declspec （dllexport）從 DLL 匯出](exporting-from-a-dll-using-declspec-dllexport.md)

- [使用 AFX_EXT_CLASS 匯出和匯入](exporting-and-importing-using-afx-ext-class.md)

- [匯出 c + + 函式以用於 C 語言可執行檔](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [判斷要使用哪一個匯出方法](determining-which-exporting-method-to-use.md)

- [使用 __declspec(dllimport) 匯入至應用程式](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [LIB 公用程式和/DEF 選項](reference/lib-reference.md)

## <a name="see-also"></a>請參閱

[匯入和匯出](importing-and-exporting.md)

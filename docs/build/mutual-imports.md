---
title: "交互匯入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bfd31cd4e5776555137daf002c076e14d4031f89
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="mutual-imports"></a>交互匯入
在匯入是雙向 （或循環），匯出或匯入到另一個可執行檔的檔案將呈現的複雜性。 例如，兩個 Dll 從匯入符號彼此相互遞迴函式類似。  
  
 交互匯入可執行檔 (通常是 Dll) 的問題是兩者都不可以建立不建置其他的第一個。 每個建置程序需要，做為輸入，其他的建置流程所產生的匯入程式庫。  
  
 解決方案是使用 LIB 公用程式 /DEF 選項時，會產生匯入程式庫，而不需建置可執行檔。 使用此公用程式，您可以建置在需要時，匯入程式庫涉及無論多少 Dll 或複雜的相依性。  
  
 處理交互匯入的一般解決方法是：  
  
1.  依次需要每個 DLL。 （任何順序是可行的雖然有些順序會更接近最佳。）如果所有需要匯入程式庫存在，而且是最新，執行來建置可執行檔 (DLL) 的連結。 這會產生匯入程式庫。 否則，執行 LIB 產生匯入程式庫。  
  
     /DEF 選項以執行 LIB 產生與其他檔案。EXP 延伸模組。 。EXP 檔案必須用來建置可執行檔的更新版本。  
  
2.  在使用後連結或 LIB 建置所有匯入程式庫，請返回並執行建置前一個步驟中沒有建置任何可執行檔的連結。 請注意，對應的.exp 檔案您必須指定連結列上。  
  
     如果您有執行 LIB 公用程式在稍早針對 DLL1 產生匯入程式庫，LIB 可能產生的檔案 DLL1.exp 以及。 建置 DLL1.dlll 時，您必須使用 DLL1.exp 做為連結的輸入。  
  
 下圖將顯示兩個相互匯入 Dll、 DLL1 和 DLL2 的解決方案。 步驟 1 是執行 LIB，與上 DLL1 /DEF 選項集合。 步驟 1 產生 DLL1.lib、 匯入程式庫和 DLL1.exp。在步驟 2 中，匯入程式庫用來建置 DLL2，會產生 DLL2 的符號匯入程式庫。 步驟 3 建立 DLL1，使用 DLL1.exp 和 DLL2.lib 做為輸入。 請注意因為 LIB 不用來建置 DLL2 的匯入程式庫不需要針對 DLL2.exp 檔。  
  
 ![使用交互匯入連結兩個 Dll](../build/media/vc37yj1.gif "vc37YJ1")  
交互匯入與連結的兩個 Dll  
  
## <a name="limitations-of-afxext"></a>_AFXEXT 的限制  
 您可以使用`_AFXEXT`您 MFC 擴充 Dll 只要您不需要多個圖層的 MFC 擴充 Dll 的前置處理器符號。 如果您有 MFC 擴充 Dll 呼叫，或衍生自類別，在您自己的 MFC 擴充 Dll，然後從 MFC 類別衍生，您必須使用您自己的前置處理器符號，以避免模稜兩可。  
  
 問題是，在 Win32 中，您必須明確宣告為任何資料**__declspec （dllexport)**是否要從 DLL 匯出和**__declspec （dllimport)**是否要從 DLL 匯入。 當您定義`_AFXEXT`，MFC 標頭，確定**AFX_EXT_CLASS**定義正確。  
  
 當您有多個圖層，一個符號例如**AFX_EXT_CLASS**不足夠，因為 MFC 擴充 DLL 可能會匯出新的類別，以及從另一個 MFC 擴充 DLL 匯入其他類別。 若要解決此問題，請使用特殊的前置處理器符號，指出您要建置 DLL 本身而非使用 DLL。 例如，假設有兩個 MFC 擴充 Dll、 A.dll 和 B.dll。 每個分別匯出 A.h 和 B.h 中的某些類別。 B.dll 會使用 A.dll 類別。 標頭檔看起來可能像這樣：  
  
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
  
 A.dll 建置時，它內建與`/D A_IMPL`而且 B.dll 建置時，它會根據`/D B_IMPL`。 每個 dll，請使用不同的符號`CExampleB`匯出和`CExampleA`建置 B.dll 時匯入。 `CExampleA`建置 A.dll 時匯出並匯入由 B.dll （或其他用戶端） 時。  
  
 使用內建時，無法執行這種類型的分層**AFX_EXT_CLASS**和`_AFXEXT`前置處理器符號。 上述的技巧來解決這個問題，方式沒有不同的是建置其 Active 技術、 資料庫和網路 MFC 擴充 Dll 時，會使用 MFC 的機制。  
  
## <a name="not-exporting-the-entire-class"></a>不會匯出整個類別  
 當您在不匯出整個類別時，您必須確定建立的 MFC 巨集的必要資料項目都正確匯出。 這可藉由來重新定義`AFX_DATA`特定類別的巨集。 這應該在完成任何您不想要匯出整個類別的時間。  
  
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
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [匯出從 DLL 使用。DEF 檔案](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 __declspec （dllexport） 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [匯出和匯入使用 AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 c + + 函式，以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [決定要使用哪一個匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [匯入應用程式使用 __declspec （dllimport）](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？  
  
-   [LIB 公用程式和 /DEF 選項](../build/reference/lib-reference.md)  
  
## <a name="see-also"></a>請參閱  
 [匯入和匯出](../build/importing-and-exporting.md)
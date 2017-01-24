---
title: "交互匯入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_AFXEXT 處理器符號"
  - "AFX_DATA"
  - "AFX_EXT_CLASS 巨集"
  - "循環匯入"
  - "DLL [C++], 匯入"
  - "可執行檔 [C++], 匯入"
  - "匯出 DLL [C++], 交互匯入"
  - "擴充 DLL [C++], 交互匯入"
  - "匯入 DLL [C++], 交互匯入"
  - "交互 DLL 匯入 [C++]"
  - "相互匯入的可執行檔 [C++]"
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 交互匯入
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

匯出或匯入到另一個可執行檔在匯入是交互 \(或循環\) 時，會發生許多併發狀況。  例如，兩個 DLL 彼此匯入符號，類似於交互遞迴的函式。  
  
 交互匯入可執行檔 \(通常是 DLL\) 的問題是兩者在建置之前必須要先建置另外一個。  每一個組建程序都需要其他組建程序所產生的匯入程式庫來當做輸入。  
  
 解決方法是使用具 \/DEF 選項的 LIB 公用程式，來產生匯入程式庫而不用建置可執行檔。  您可以使用這個公用程式來建置所有需要的匯入程式庫，而不管涉及多少 DLL 或相依性有多複雜。  
  
 處理交互匯入一般的解決方法是：  
  
1.  依序處理每一個 DLL \(可以使用任何順序，雖然有些順序會較佳\)。如果所有需要匯入的程式庫都存在而且是最新的，請執行 LINK 來建置可執行檔 \(DLL\)。  這會產生匯入程式庫。  否則，請執行 LIB 來產生匯入程式庫。  
  
     執行具有 \/DEF 選項的 LIB 會產生具 .EXP 副檔名的其他檔案。  該 .EXP 檔案稍後必須用來建置可執行檔。  
  
2.  使用 LINK 或 LIB 來建置所有的匯入程式庫之後，請返回並執行 LINK 來建置任何在上一步驟沒有建置的可執行檔。  請注意，相對應的 .exp 檔案必須在 LINK 行指定。  
  
     如果您在為 DLL1 產生匯入程式庫之前已經先執行 LIB 公用程式，LIB 也將會產生 DLL1.exp 檔案。  您必須在建置 DLL1.dll 時，使用 DLL1.exp 來當做對 LINK 的輸入。  
  
 下列範例將示範兩個相互匯入的 DLL \(DLL1 和 DLL2\) 方案。  步驟 1 是以 \/DEF 選項組在 DLL1 上執行 LIB。  步驟 1 產生 DLL1.lib、匯入程式庫和 DLL1.exp。  在步驟 2 裡，匯入程式庫是用來建置 DLL2，然後它會為 DLL2 的符號產生匯入程式庫。  步驟 3 藉著將 DLL1.exp 和 DLL2.lib 當成輸入，建置 DLL1。  請注意，DLL2 的 .exp 檔不是必須的，因為 LIB 不會用於建置 DLL2 的匯入程式庫。  
  
 ![使用交互匯入來連結兩個 DLL](../build/media/vc37yj1.png "vc37YJ1")  
連結具交互匯入的兩個 DLL  
  
## \_AFXEXT 的限制  
 只要您沒有多層的擴充 DLL，您就可以為您的擴充 DLL 使用 `_AFXEXT` 前置處理器符號。  如果您的擴充 DLL 呼叫或衍生自您自己之擴充 DLL 裡的類別，接著又衍生自 MFC 類別，您必須使用自己的前置處理器符號來避免模稜兩可 \(Ambiguity\) 的情形。  
  
 問題是因為您必須在 Win32 中將任何從 DLL 匯出的資料明確地宣告為 **\_\_declspec\(dllexport\)**，而在從 DLL 匯入則宣告為 **\_\_declspec\(dllimport\)**。  當您定義 `_AFXEXT` 時，MFC 標頭檔會確定 **AFX\_EXT\_CLASS** 已正確地定義。  
  
 當您有多層時，一個符號是不夠的 \(如 **AFX\_EXT\_CLASS**\)，因為擴充 DLL 可能匯出新類別以及從另一個擴充 DLL 匯入其他類別。  若要解決這個問題，請使用特殊的前置處理器符號，指示您是在建置 DLL 本身而非使用 DLL。  例如，請想像兩個擴充 DLL，A.dll 和 B.dll。  它們各自在 A.h 和 B.h 裡匯出一些類別。  B.dll 會使用 A.dll 的類別。  標頭檔會看起來會類似下列所示：  
  
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
  
 A.dll 在建置時是以 `/D A_IMPL` 建置，而 B.dll 則是以 `/D B_IMPL` 建置。  因為已經對每一個 DLL 使用不同的符號，所以建置 B.dll 時會匯出 `CExampleB` 且匯入 `CExampleA`。  `CExampleA` 在建置 A.dll 時是匯出，而用於 B.dll \(或其他的一些用戶端\) 時則是匯入。  
  
 在使用內建的 **AFX\_EXT\_CLASS** 和 `_AFXEXT` 前置處理器符號時，無法進行這類型的分層。  上述技術可解決這種問題，其不同於 MFC 本身在建置 Active 技術、資料庫和網路擴充 DLL 時所使用的機制。  
  
## 不要匯出整個類別  
 您必須在不是匯出整個類別時，確定已正確匯出 MFC 巨集所建立的必要資料項目。  這個部分可以藉由可重新定義 `AFX_DATA` 成為您的特定類別之巨集來完成。  這個工作應該在每次您沒有匯出整個類別時執行。  
  
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
  
### 您想要執行甚麼工作？  
  
-   [從 DLL 匯出](../build/exporting-from-a-dll.md)  
  
-   [使用 .DEF 檔從 DLL 匯出](../build/exporting-from-a-dll-using-def-files.md)  
  
-   [使用 \_\_declspec\(dllexport\) 從 DLL 匯出](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [使用 AFX\_EXT\_CLASS 匯出和匯入](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [匯出 C\+\+ 函式以用於 C 語言可執行檔](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [判斷要使用哪一種匯出方法](../build/determining-which-exporting-method-to-use.md)  
  
-   [使用 \_\_declspec\(dllimport\) 匯入至應用程式](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [LIB 公用程式和 \/DEF 選項](../build/reference/lib-reference.md)  
  
## 請參閱  
 [匯入和匯出](../build/importing-and-exporting.md)
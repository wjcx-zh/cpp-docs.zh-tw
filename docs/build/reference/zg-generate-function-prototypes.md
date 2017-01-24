---
title: "/Zg (產生函式原型) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/zg"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zg 編譯器選項 [C++]"
  - "函式原型, 產生函式原型編譯器選項"
  - "產生函式原型編譯器選項"
  - "Zg 編譯器選項 [C++]"
  - "-Zg 編譯器選項 [C++]"
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Zg (產生函式原型)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已移除。 為原始程式檔中定義的每個函式建立函式原型，但不會編譯原始程式檔。  
  
## 語法  
  
```  
/Zg  
```  
  
## 備註  
 此編譯器選項已無法使用。 已從 Visual C\+\+ 2015 將其移除。 此頁面保留給舊版 Visual C \+\+ 的使用者。  
  
 函式原型包括函式的傳回型別和引數型別清單。 引數型別清單是建立自函式的型式參數型別。 任何已經存在於原始程式檔中的函式原型都會被忽略。  
  
 原型清單已寫入標準輸出。 您將會發現這份清單有助於驗證函式的實際引數和型式參數是否相容。 您可將標準輸出重新導向至檔案，以儲存清單。 然後您可以使用 **\#include** 讓函式原型清單成為原始程式檔的一部分。 這樣做會讓編譯器執行引數型別檢查。  
  
 若您使用 **\/Zg** 選項，且您的程式包含具有結構、列舉或等位型別 \(或這些型別的指標\) 之型式參數，則每個結構、列舉或等位型別的宣告都必須具有標記 \(名稱\)。 在下列範例中，標記名稱為 `MyStruct`。  
  
```  
// Zg_compiler_option.c  
// compile with: /Zg  
typedef struct MyStruct { int i; } T2;  
void f2(T2 * t) {}  
```  
  
 **\/Zg** 已被取代。 Visual C\+\+ 編譯器計劃移除對舊版 C 樣式程式碼的支援。 如需詳細資訊，請參閱 [Visual C\+\+ 2005 中已取代的編譯器選項](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[屬性頁\] 對話方塊。 如需詳細資訊，請參閱[如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[C\/C\+\+\] 資料夾。  
  
3.  按一下 \[命令列\] 屬性頁。  
  
4.  在 \[其他選項\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
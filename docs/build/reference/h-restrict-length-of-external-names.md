---
title: "/H (限制外部名稱的長度) | Microsoft Docs"
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
  - "/h"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/H 編譯器選項 [C++]"
  - "外部名稱"
  - "H 編譯器選項 [C++]"
  - "-H 編譯器選項 [C++]"
  - "公用名稱長度"
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /H (限制外部名稱的長度)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

限制外部名稱的長度。  
  
## 語法  
  
```  
/Hnumber  
```  
  
## Arguments  
 `number`  
 是指定程式中所允許外部名稱的最大長度。  
  
## 備註  
 根據預設，外部 \(公用\) 名稱的長度為 2,047 個字元。  這對於 C 和 C\+\+ 程式都適用。  使用 **\/H** 只能減少識別項的最大允許長度，不能增加。  **\/H** 和 `number` 之間的空格是選擇性的。  
  
 如果程式包含的外部名稱比 `number` 長，多出來的字元將會被忽略。  如果編譯程式時不使用 **\/H**，而且如果識別項含有超過 2,047 個字元，那麼編譯器將會產生[嚴重錯誤 C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)。  
  
 此一長度限制包括任何編譯器建立的前置底線 \(\_\) 或 at 符號 \(@\)。  這些字元是識別項的一部分而且也會佔用一個有效位置。  
  
-   編譯器會對 `__cdecl` \(預設\) 和 `__stdcall` 呼叫慣例修改的名稱加上一個前置底線 \(\_\)，並且對 `__fastcall` 呼叫慣例修改的名稱加上一個 at 符號 \(@\)。  
  
-   編譯器會將引數大小資訊附加到 `__fastcall` 和 `__stdcall` 呼叫慣例修改的名稱後面，並且將型別資訊加入到 C\+\+ 名稱。  
  
 在下列各狀況下，您可能會覺得 **\/H** 很有用：  
  
-   當您建立混合語言或可移植的程式時。  
  
-   當您使用對外部識別項長度有限制的工具時。  
  
-   當您想要限制偵錯組建中符號使用的空間數量時。  
  
 以下範例會示範，如果識別項長度限制過當的話，使用 **\/H** 如何可能會實際引發錯誤：  
  
```  
// compiler_option_H.cpp  
// compile with: /H5  
// processor: x86  
// LNK2005 expected  
void func1(void);  
void func2(void);  
  
int main() { func1(); }  
  
void func1(void) {}  
void func2(void) {}  
```  
  
 如果有預先定義的編譯器識別項，使用 **\/H** 選項時也必須非常小心。  如果最大識別項長度太小，有些預先定義的識別項會和某些程式庫函式呼叫一樣無法解析。  舉例來講，如果使用了 `printf` 函式，並且在編譯時期指定了選項 **\/H5**，則為了參考 `printf` 就會建立符號 **\_prin**，但是在程式庫裡將找不到這個符號。  
  
 使用 **\/H** 與 [\/GL \(整個程式最佳化\)](../../build/reference/gl-whole-program-optimization.md) 不相容。  
  
 **\/H** 已被取代。因為最長的長度限制已經增加，所以已不再需要 **\/H**。如需詳細資訊，請參閱[Deprecated Compiler Options in Visual C\+\+ 2005](http://msdn.microsoft.com/zh-tw/aa59fce3-50b8-4f66-9aeb-ce09a7a84cce)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**命令列**\] 屬性頁。  
  
4.  在 \[**其他選項**\] 方塊中，輸入編譯器選項。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
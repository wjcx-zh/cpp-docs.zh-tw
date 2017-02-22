---
title: "/Zc:strictStrings (停用字串常值型別轉換) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc:strictStrings"
  - "strictStrings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc 編譯器選項 (C++)"
  - "/Zc:strictStrings"
  - "strictStrings"
  - "Zc 編譯器選項 (C++)"
  - "-Zc 編譯器選項 (C++)"
ms.assetid: b7eb3f3b-82c1-48a2-8e63-66bad7397b46
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /Zc:strictStrings (停用字串常值型別轉換)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定時，對於使用字串常值初始的指標，編譯器需要嚴格的 `const` 限定一致性。  
  
## 語法  
  
```  
/Zc:strictStrings[-]  
```  
  
## 備註  
 如果指定 **\/Zc:strictStrings**，則編譯器會對字串常值，強制執行標準 C\+\+ `const` 限定，根據宣告情況，限定為 'array of `const` `char`' 或 'array of `const` `wchar_t`' 型別。  字串常值不可變，如果嘗試修改其內容，則會導致執行階段存取違規錯誤。  您必須將字串指標宣告為 `const`，以使用字串常值來對其進行初始化，或者使用明確的 `const_cast`，對非 `const` 指標進行初始化。  根據預設，或者如果指定 **\/Zc:strictStrings\-**，則編譯器不會對使用字串常值初始化的字串指標，強制執行標準 C\+\+ `const` 限定。  
  
 使用 **\/Zc:strictStrings** 選項，可以防止編譯不正確的程式碼。  此範例顯示簡單的宣告錯誤如何導致執行階段損毀：  
  
```cpp  
// strictStrings_off.cpp  
// compile by using: cl /W4 strictStrings_off.cpp  
int main() {  
   wchar_t* str = L"hello";  
   str[2] = L'a'; // run-time error: access violation  
}  
```  
  
 當啟用 **\/Zc:strictStrings** 時，相同的程式碼會報告 `str` 宣告中的錯誤。  
  
```cpp  
// strictStrings_on.cpp  
// compile by using: cl /Zc:strictStrings /W4 strictStrings_on.cpp  
int main() {  
   wchar_t* str = L"hello"; // error: Conversion from string literal   
   // loses const qualifier  
   str[2] = L'a';   
}  
```  
  
 如果您使用 `auto`，來宣告字串指標，則編譯器會為您建立正確的 `const` 指標類型宣告。  如果嘗試修改 `const` 指標的內容，則編譯器會報告錯誤。  
  
> [!NOTE]
>  [!INCLUDE[cpp_dev12_long](../../build/reference/includes/cpp_dev12_long_md.md)] 中的標準 C\+\+ 程式庫在偵錯組建中不支援 **\/Zc:strictStrings** 編譯器選項。  如果您在組建輸出中看到數個 [C2665](../../error-messages/compiler-errors-2/compiler-error-c2665.md) 錯誤，則這可能是原因。  
  
 如需 Visual C\+\+ 中一致性問題的詳細資訊，請參閱[非標準行為](../../cpp/nonstandard-behavior.md)。  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取 \[**C\/C\+\+**\] 資料夾。  
  
3.  選取 \[**命令列**\] 屬性頁。  
  
4.  修改 \[其他選項\] 屬性，以包括 `/Zc:strictStrings`，然後選擇 \[確定\]。  
  
## 請參閱  
 [\/Zc \(一致性\)](../../build/reference/zc-conformance.md)
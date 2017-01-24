---
title: "selectany | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "selectany_cpp"
  - "selectany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 關鍵字 [C++], selectany"
  - "selectany __declspec 關鍵字"
ms.assetid: 9c353017-5a42-4f50-b741-bd13da1ce84d
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# selectany
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 告訴編譯器宣告的全域資料項目 \(變數或物件\) 是挑選任一個 \(Pick\-any\) COMDAT \(封裝函式\)。  
  
## 語法  
  
```  
  
__declspec( selectany ) declarator  
```  
  
## 備註  
 在連結時，如果看見多個定義的 COMDAT，則連結器會挑選一個定義並捨棄其餘定義。  如果已選取連結器選項 [\/OPT:REF](../build/reference/opt-optimizations.md) \(最佳化\)，則 COMDAT 刪除作業將會發生，並移除連結器輸出中所有未參考的資料項目。  
  
 宣告中的建構函式以及由全域函式或靜態方法進行的指派不會建立參考，也不會阻止 \/OPT:REF 刪除作業。  來自這類程式碼的副作用不應取決於不存在其他資料參考時。  
  
 對於動態初始化的全域物件，`selectany` 也會捨棄未參考物件的初始化程式碼。  
  
 全域資料項目通常只能在 EXE 或 DLL 專案中初始化一次。  當相同標頭出現在多個原始程式檔中時，可以使用 `selectany` 初始化標頭所定義的全域資料。  C 和 C\+\+ 編譯器中都可以使用 `selectany`。  
  
> [!NOTE]
>  `selectany` 只能套用至外部可見的全域資料項目的實際初始化。  
  
## 範例  
 這段程式碼將示範如何使用 `selectany` 屬性：  
  
```  
//Correct - x1 is initialized and externally visible   
__declspec(selectany) int x1=1;  
  
//Incorrect - const is by default static in C++, so   
//x2 is not visible externally (This is OK in C, since  
//const is not by default static in C)  
const __declspec(selectany) int x2 =2;  
  
//Correct - x3 is extern const, so externally visible  
extern const __declspec(selectany) int x3=3;  
  
//Correct - x4 is extern const, so it is externally visible  
extern const int x4;  
const __declspec(selectany) int x4=4;  
  
//Incorrect - __declspec(selectany) is applied to the uninitialized  
//declaration of x5  
extern __declspec(selectany) int x5;  
  
// OK: dynamic initialization of global object  
class X {  
public:  
X(int i){i++;};  
int i;  
};  
  
__declspec(selectany) X x(1);  
```  
  
## 範例  
 這段程式碼示範如何在您同時使用 [\/OPT: ICF](../build/reference/opt-optimizations.md) 連結器選項時，使用 `selectany` 屬性確保資料的 COMDAT 摺疊。  請注意，資料必須以 `selectany` 標記並且放入 **const** \(唯讀\) 區段中。  您必須明確指定唯讀區段。  
  
```  
// selectany2.cpp  
// in the following lines, const marks the variables as read only  
__declspec(selectany) extern const int ix = 5;  
__declspec(selectany) extern const int jx = 5;  
int main() {  
   int ij;  
   ij = ix + jx;  
}  
```  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)
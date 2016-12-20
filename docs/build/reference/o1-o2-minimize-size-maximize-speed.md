---
title: "/O1、/O2 (最小大小、最快速度) | Microsoft Docs"
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
  - "/o2"
  - "/o1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/O1 編譯器選項 [C++]"
  - "/O2 編譯器選項 [C++]"
  - "快程式碼"
  - "maximize speed 編譯器選項 [C++]"
  - "minimize size 編譯器選項 [C++]"
  - "O1 編譯器選項 [C++]"
  - "-O1 編譯器選項 [C++]"
  - "O2 編譯器選項 [C++]"
  - "-O2 編譯器選項 [C++]"
  - "小的程式碼"
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /O1、/O2 (最小大小、最快速度)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

選取一組預先定義而能夠影響檔案大小和速度的選項。  
  
## 語法  
  
```  
/O1  
/O2  
```  
  
## 備註  
 下表描述了 **\/O1** 和 **\/O2**。  
  
|選項|相當於|Comment|  
|--------|---------|-------------|  
|**\/O1** \(最小化程式碼\)|**\/Og \/Os \/Oy \/Ob2 \/Gs \/GF \/Gy**|在大多數情況下會建立最小的程式碼。|  
|**\/O2** \(最大化速度\)|**\/Og \/Oi \/Ot \/Oy \/Ob2 \/Gs \/GF \/Gy**|在大多數情況下建立最快的程式碼。\(發行組建的預設設定\)。|  
  
 **\/O1** 和 **\/O2** 也會啟用「具名傳回值」最佳化，以排除堆疊式傳回值的複製建構函式和解構函式，  您可以參考下列範例。`Test` 函式不會建立複製建構函式或解構函式，  您可以加入輸入陳述式至建構函式、解構函式和複製建構函式，以了解執行程式時「具名傳回值」最佳化的效果。  如需詳細資訊，請參閱 [名為 Visual C\+\+ 2005 中的傳回值最佳化](http://go.microsoft.com/fwlink/?linkid=131571)。  
  
```  
// O1_O2_NRVO.cpp  
// compile with: /O1  
struct A {  
   A() {}  
   ~A() {}  
   A(const A& aa) {}  
};  
  
A Test() {  
   A a;  
   return a;  
}  
int main() {  
   A aa;  
   aa = Test();  
}  
```  
  
 **x86 專屬資訊**  
  
 這些選項隱含了框架指標省略 \([\/Oy](../../build/reference/oy-frame-pointer-omission.md)\) 選項的使用。  
  
 **x86 專屬資訊結束**  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**最佳化**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [\/EH \(例外狀況處理模型\)](../../build/reference/eh-exception-handling-model.md)
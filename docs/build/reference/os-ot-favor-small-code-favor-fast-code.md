---
title: "/Os、/Ot (偏好小的程式碼、偏好快的程式碼) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLWCECompilerTool.FavorSizeOrSpeed"
  - "/os"
  - "VC.Project.VCCLCompilerTool.FavorSizeOrSpeed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Os 編譯器選項 [C++]"
  - "/Ot 編譯器選項 [C++]"
  - "快程式碼"
  - "偏好快的程式碼編譯器選項 [C++]"
  - "偏好小的程式碼編譯器選項 [C++]"
  - "Os 編譯器選項 [C++]"
  - "-Os 編譯器選項 [C++]"
  - "Ot 編譯器選項 [C++]"
  - "-Ot 編譯器選項 [C++]"
  - "小機器碼"
ms.assetid: 9a340806-fa15-4308-892c-355d83cac0f2
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /Os、/Ot (偏好小的程式碼、偏好快的程式碼)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將 EXE 和 DLL 的大小最小化或最大化。  
  
## 語法  
  
```  
/Os  
/Ot  
```  
  
## 備註  
 **\/Os** \(偏好小的程式碼\) 是指示編譯器大小最佳化優先於速度最佳化，將可執行檔和 DLL 的大小最小化。  編譯器可以將許多 C 和 C\+\+ 建構縮減為功能類似的機器碼順序。  有時候，這些差異也會在大小與速度之間提供一些取捨。  **\/Os** 和 **\/Ot** 選項可以讓您指定偏好其中一種：  
  
 **\/Ot** \(偏好快的程式碼\) 是指示編譯器速度最佳化優先於大小最佳化，讓 .exe 檔案和 DLL 達到最快速度 \(這是預設值\)。編譯器可以將許多 C 和 C\+\+ 建構縮減為功能類似的機器碼順序。  有時候這些差異也能提供在大小與速度之間取捨。  \/Ot 選項是隱含在最快速執行效能 \([\/O2](../../build/reference/o1-o2-minimize-size-maximize-speed.md)\) 選項之中。  **\/O2** 選項會結合幾個選項，以產生非常快速的程式碼。  
  
 如果您使用 **\/Os** 或 **\/Ot**，則也必須指定 [\/Og](../../build/reference/og-global-optimizations.md)，將程式碼最佳化。  
  
> [!NOTE]
>  從程式碼剖析測試回合所收集的資訊，會覆寫因您指定 **\/Ob**、**\/Os** 或 **\/Ot** 而作用中的最佳化。  如需詳細資訊，請參閱 [特性指引最佳化](../../build/reference/profile-guided-optimizations.md)。  
  
 **x86 專屬資訊**  
  
 以下範例程式碼示範了 \[偏好小的程式碼\] \(**\/Os**\) 選項和 \[偏好快的程式碼\] \(**\/Ot**\) 選項之間的差異：  
  
> [!NOTE]
>  以下描述使用 **\/Os** 或 **\/Ot** 時必須有的行為。  不過，發行版本的編譯器行為可能會對以下的程式碼產生不同的最佳化。  
  
```  
/* differ.c  
  This program implements a multiplication operator  
  Compile with /Os to implement multiply explicitly as multiply.  
  Compile with /Ot to implement as a series of shift and LEA instructions.  
*/  
int differ(int x)  
{  
    return x * 71;  
}  
```  
  
 如下列機器碼片段中所示，當 DIFFER.c 針對大小 \(**\/Os**\) 編譯時，編譯器會將傳回陳述式中的乘法運算式明確地實作為乘法，以產生較短但較慢的程式碼順序：  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
imul   eax, 71                  ; 00000047H  
```  
  
 或者，當 DIFFER.c 針對速度 \(**\/Ot**\) 編譯時，編譯器會將傳回陳述式中的乘法運算式實作為一系列移位 \(Shift\) 和 `LEA` 指令，以產生快速但較長的程式碼順序：  
  
```  
mov    eax, DWORD PTR _x$[ebp]  
mov    ecx, eax  
shl    eax, 3  
lea    eax, DWORD PTR [eax+eax*8]  
sub    eax, ecx  
```  
  
 **x86 專屬資訊結束**  
  
### 在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  按一下 \[**C\/C\+\+**\] 資料夾。  
  
3.  按一下 \[**最佳化**\] 屬性頁。  
  
4.  修改 \[**偏好大小或速度**\] 屬性。  
  
### 若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.FavorSizeOrSpeed%2A>。  
  
## 請參閱  
 [\/O 選項 \(最佳化程式碼\)](../../build/reference/o-options-optimize-code.md)   
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)
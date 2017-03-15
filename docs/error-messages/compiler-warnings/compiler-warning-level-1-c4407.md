---
title: "編譯器警告 (層級 1) C4407 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4407"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4407"
ms.assetid: 32bc2c21-363a-4bb8-b486-725faeaededc
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 編譯器警告 (層級 1) C4407
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不同成員指標表示法之間的轉換，編譯器可能會產生不正確的程式碼  
  
 偵測到不正確的轉換。  
  
 在 Visual C\+\+ 2005 中完成一致性處理的結果可能會產生 C4407。  成員指標現在需要有限定名稱和運算子的位址 \(&\)。  
  
 如果您在多重繼承成員指標與單一繼承成員指標轉換，可能會發生 C4407。  這項作業有時能成功，但有時又無法成功，因為單一繼承成員指標表示無法存放足夠的資訊。  使用 **\/vmm** 編譯可能會有幫助 \(如需詳細資訊，請參閱 [\/vmm、\/vms、\/vmv \(一般用途表示\)](../../build/reference/vmm-vms-vmv-general-purpose-representation.md)\)。  您也可以嘗試重新排列基底類別；因為基底類別位於從衍生類別開始的非零位移，編譯器偵測到轉換中資訊遺失。  
  
 下列範例會產生 C4407：  
  
```  
// C4407.cpp  
// compile with: /W1 /c  
struct C1 {};  
struct C2 {};  
struct C3 : C1, C2 {};  
  
typedef void(C3::*PMF_C3)();  
typedef void(C2::*PMF_C2)();  
  
PMF_C2 f1(PMF_C3 pmf) {  
   return (PMF_C2)pmf;   // C4407, change type of cast,  
   // or reverse base class inheritance of C3 (i.e. : C2, C1)  
}  
```
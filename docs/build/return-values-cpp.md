---
title: "傳回值 (C++) | Microsoft Docs"
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
ms.assetid: 53583524-b337-4228-a9c6-c9bf516babe8
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 傳回值 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可納入 64 位元的純量傳回值將會透過 RAX 傳回，其中包括 \_\_m64 類型。  非純量類型包括浮點數、雙精度浮點數和向量類型，例如 [\_\_m128](../cpp/m128.md)、[\_\_m128i](../cpp/m128i.md)、[\_\_m128d](../cpp/m128d.md) 將於 XMM0 中傳回。  對於 RAX 或 XMM0 中傳回的值，其中未使用之位元的狀態尚未定義。  
  
 使用者定義的類型可透過全域函式和靜態成員函式的值傳回。  使用者定義的類型若要由 RAX 中的值傳回，其長度必須為 1、2、4、8、16、32 或 64 個位元；沒有使用者定義的建構函式、解構函式或複製指派運算子；沒有私用或受保護的非靜態資料成員；沒有參考類型的非靜態資料成員；沒有基底類別；沒有虛擬函式；亦沒有不符合這些需求的資料成員。  \(這基本上是 C\+\+03 POD 類型的定義。  因為在 C\+\+11 標準中的定義已經變更，所以我們不建議將 `std::is_pod` 用於這項測試。\) 否則，呼叫端會負責配置記憶體，並且為傳回值傳遞一個指標做為第一個引數。  後續的引數將向右移一個引數。  在 RAX 中的被呼叫端必須傳回相同的指標。  
  
 這些範例展示有指定之宣告的函式如何傳遞參數和傳回值：  
  
## 傳回值 1 \- 64 位元結果的範例  
  **\_\_int64 func1\(int a, float b, int c, int d, int e\);**  
**\/\/ 呼叫端在 RCX 中傳遞 a，在 XMM1 中傳遞 b，在 R8 中傳遞 c，在 R9 中傳遞 d，並將 e 推送至堆疊，**  
**\/\/ 被呼叫端會在 RAX 中傳回 \_\_int64 結果。**   
## 傳回值 2 \- 128 位元結果的範例  
  **\_\_m128 func2\(float a, double b, int c, \_\_m64 d\);**   
**\/\/ 呼叫端在 xmm0 中傳遞 a，在 XMM1 中傳遞 b，在 R8 中傳遞 c，在 R9 中傳遞 d，**  
**\/\/ 被呼叫端在 XMM0 中傳回 \_\_m128 結果。**   
## 傳回值 3 – 由指標產生之使用者類型結果的範例  
  **struct Struct1 {**  
 **int j, k, l;    \/\/ Struct1 超過 64 個位元。  };**  
**Struct1 func3\(int a, double b, int c, float d\);**   
**\/\/ 呼叫端爲傳回的 Struct1 配置記憶體，並在 RCX 中傳遞指標，**  
**\/\/ 在 RDX 中傳遞 a，在 XMM2 中傳遞 b，在 R9 中傳遞 c，並將 d 推送到堆疊；**   
**\/\/ 被呼叫端會在 RAX 中將指標傳回 Struct1 結果。**    
## 傳回值 4 – 由值產生之使用者類型結果的範例  
  **struct Struct2 {**  
 **int j, k;    \/\/ Struct2 可納入 64 個位元，並符合以值傳回的需求。  };**  
**Struct2 func4\(int a, double b, int c, float d\);**   
**\/\/ 呼叫端在 RCX 中傳遞 a，在 XMM1 中傳遞 b，在 R8 中傳遞 c，在 XMM3 中傳遞 d；**   
**\/\/ 被呼叫端會在 RAX 中將 Struct2 結果以值傳回。**    
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)
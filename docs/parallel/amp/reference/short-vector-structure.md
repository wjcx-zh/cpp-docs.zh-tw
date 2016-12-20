---
title: "short_vector 結構 | Microsoft Docs"
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
  - "amp_short_vectors/Concurrency::graphics::short_vector"
dev_langs: 
  - "C++"
ms.assetid: e4f50b8f-1150-437d-b58c-79c5fb883708
caps.latest.revision: 7
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# short_vector 結構
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

short\_vector 提供對於 short vectors 泛型程式設計非常有用的 metaprogramming 定義。  
  
## 語法  
  
```  
template<  
   typename _Scalar_type,  
   int _Size  
>  
struct short_vector;  
template<>  
struct short_vector<unsigned int, 1>;  
template<>  
struct short_vector<unsigned int, 2>;  
template<>  
struct short_vector<unsigned int, 3>;  
template<>  
struct short_vector<unsigned int, 4>;  
template<>  
struct short_vector<int, 1>;  
template<>  
struct short_vector<int, 2>;  
template<>  
struct short_vector<int, 3>;  
template<>  
struct short_vector<int, 4>;  
template<>  
struct short_vector<float, 1>;  
template<>  
struct short_vector<float, 2>;  
template<>  
struct short_vector<float, 3>;  
template<>  
struct short_vector<float, 4>;  
template<>  
struct short_vector<unorm, 1>;  
template<>  
struct short_vector<unorm, 2>;  
template<>  
struct short_vector<unorm, 3>;  
template<>  
struct short_vector<unorm, 4>;  
template<>  
struct short_vector<norm, 1>;  
template<>  
struct short_vector<norm, 2>;  
template<>  
struct short_vector<norm, 3>;  
template<>  
struct short_vector<norm, 4>;  
template<>  
struct short_vector<double, 1>;  
template<>  
struct short_vector<double, 2>;  
template<>  
struct short_vector<double, 3>;  
template<>  
struct short_vector<double, 4>;  
```  
  
#### 參數  
 `_Scalar_type`  
 `_Size`  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`type`||  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[short\_vector::short\_vector 建構函式](../Topic/short_vector::short_vector%20Constructor.md)||  
  
## 繼承階層架構  
 `short_vector`  
  
## 需求  
 **標頭:** amp\_short\_vectors.h  
  
 **命名空間:**  Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)
---
title: "緩衝區溢位 | Microsoft Docs"
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
  - "緩衝區溢位 [C++]"
  - "緩衝區 [C++], 字元大小"
  - "MBCS [C++], 緩衝區溢位"
ms.assetid: f2b7e40a-f02b-46d8-a449-51d26fc0c663
caps.latest.revision: 8
caps.handback.revision: 8
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# 緩衝區溢位
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您將字元放入緩衝區時，改變字元大小會造成問題。  考慮下列程式碼，將字元從字串 `sz` 複製到緩衝區 `rgch`：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
    rgch[ cb++ ] = *sz++;  
```  
  
 問題是：最後複製的位元組是前導位元組嗎？  下列程式碼不能解決問題，因為它有可能溢位緩衝區：  
  
```  
cb = 0;  
while( cb < sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 `_mbccpy` 呼叫嘗試採取正確行動 — 複製完整字元，不論它是 1 個或 2 個位元組。  但是它並沒有考慮到，如果這個字元是 2 個位元組寬，則最後複製的字元可能不配合緩衝區。  正確的解決方法是：  
  
```  
cb = 0;  
while( (cb + _mbclen( sz )) <= sizeof( rgch ) )  
{  
    _mbccpy( rgch + cb, sz );  
    cb += _mbclen( sz );  
    sz = _mbsinc( sz );  
}  
```  
  
 此程式碼在迴圈測試裡測試可能的緩衝區溢位，使用 `_mbclen` 來測試目前由 `sz` 所指的字元大小。  藉著呼叫 `_mbsnbcpy` 函式，您可用單行程式碼取代 `while` 迴圈裡的程式碼。  例如：  
  
```  
_mbsnbcpy( rgch, sz, sizeof( rgch ) );  
```  
  
## 請參閱  
 [MBCS 程式設計提示](../text/mbcs-programming-tips.md)
---
title: "編譯器限制 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, limits for language constructs
ms.assetid: f1fa59c6-55b4-414b-80c5-3df72952160d
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 986a158ea74e56a0e52c1ffff77f83b8ede71ef5
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="compiler-limits"></a>編譯器限制
C++ 標準會建議各種語言的建構限制。 下列是 Visual C++ 編譯器未實作所建議之限制的案例。 第一個數字是 ISO C++ 11 標準 (INCITS/ISO/IEC 14882-2011[2012], Annex B) 所建立的限制，第二個數字是 Visual C++ 所實作的限制：  
  
-   巢狀層級的複合陳述式、 反覆項目控制結構和選取控制項結構的 c + + 標準： 256，Visual c + + 編譯器： 視陳述式的巢狀，但通常介於 100 和 110 之間的組合。  
  
-   參數單一巨集定義中的 c + + 標準： 256，Visual c + + 編譯器： 127。  
  
-   引數，在一個巨集引動過程-c + + 標準： 256，Visual c + + 編譯器： 127。  
  
-   中字元的字元字串常值或寬字串常值 （串連之後）-c + + 標準： 65536，Visual c + + 編譯器： 65535 的單一位元組字元，包括`null`結束字元和 32767 雙位元組字元，包括`null`結束字元。  
  
-   層級的巢狀的類別、 結構或等位定義在單一`struct-declaration-list`-c + + 標準： 256，Visual c + + 編譯器： 16。  
  
-   成員初始設定式中建構函式定義為 c + + 標準： 6144，Visual c + + 編譯器： 至少 6144。  
  
-   範圍限定性條件的識別碼-c + + 標準： 256，Visual c + + 編譯器： 127。  
  
-   巢狀`extern`規格的 c + + 標準： 1024，Visual c + + 編譯器： 9 (不計算隱含`extern`規格在全域範圍或 10，如果您計算隱含`extern`在全域範圍內的規格..  
  
-   樣板引數的樣板宣告-c + + 標準： 1024，Visual c + + 編譯器： 2046年。  
  
## <a name="see-also"></a>另請參閱  
 [非標準行為](../cpp/nonstandard-behavior.md)

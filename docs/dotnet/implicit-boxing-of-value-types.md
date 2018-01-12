---
title: "實值類型的隱含 Boxing |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0c4725cdd7e8630131f77e02eedc2af14a469d20
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="implicit-boxing-of-value-types"></a>實值類型的隱含 Boxing
實值類型的 boxing 已從 Managed Extensions for c + + Visual c + +。  
  
 在語言設計中，我們理性功能的實際經驗，並在實務上，這是錯誤。 比方說，在原始語言設計多個繼承，Stroustrup 決定在衍生的類別建構函式，無法初始化虛擬基底類別的子物件，並因此語言所需的任何類別做為虛擬基底類別必須定義預設建構函式。 就會叫用任何後續的虛擬衍生的預設建構函式。  
  
 虛擬基底類別階層架構的問題是共用的虛擬子物件的初始化負責移位使用每個後續衍生。 例如，如果定義的基底類別初始化需要的緩衝區，而使用者指定的緩衝區大小配置可能會傳遞做為引數建構函式。 然後，我會提供兩個的後續虛擬衍生，如果呼叫它們`inputb`和`outputb`，每個提供特定值的基底類別建構函式。 現在，當我衍生`in_out`類別同時從`inputb`和`outputb`，都不共用的虛擬基底類別的子物件的這些值明智允許評估。  
  
 因此，在原始語言設計中，Stroustrup 不允許明確初始化成員初始設定清單中的衍生的類別建構函式的虛擬基底類別。 儘管這解決問題，在實務上無法導向虛擬基底類別初始化證實了無法實行。 National Institute 的健全狀況，Keith Gorlen 者必須實作稱為 nihcl SmallTalk 集合程式庫的免費軟體版本，已在說服 Stroustrup 他已準備好更有彈性的語言設計原則語音。  
  
 物件導向的階層式設計的原則會保存在衍生的類別應該考量本身只與非私用實作直接基底類別。 若要支援虛擬繼承彈性初始化設計，Stroustrup 必須違反此原則。 在階層中最常衍生的類別負責不論深度所有的虛擬子物件初始化，到它，就會發生的階層。 例如，`inputb`和`outputb`都負責明確初始化其即時虛擬基底類別。 當`in_out`衍生自兩者`inputb`和`outputb`，`in_out`負責初始化一次移除虛擬基底類別，並初始化進行中明確`inputb`和`outputb`是隱藏的。  
  
 這提供彈性，由語言的開發人員，代價是複雜的語意。 此項負擔的複雜功能移除了如果要限制不具有狀態，並且只允許指定介面的虛擬基底類別。 這是 c + + 中的建議的設計慣用語。 Clr 程式設計中，它就會引發與介面類型的原則。  
  
 以下是簡單的程式碼範例-，並在此情況下，無須明確的 boxing:  
  
```  
// Managed Extensions for C++ requires explicit __box operation  
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };  
Object* myObjArray __gc[] = {   
   __box(26), __box(27), __box(28), __box(29), __box(30)  
};  
  
Console::WriteLine( "{0}\t{1}\t{2}", __box(0),  
   __box(my1DIntArray->GetLowerBound(0)),  
   __box(my1DIntArray->GetUpperBound(0)) );  
```  
  
 如您所見，還有許多的 boxing 進行的作業。 在 Visual c + + 中，實值型別都是隱含 boxing:  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## <a name="see-also"></a>請參閱  
 [實值類型和它們的行為 (C + + /CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Boxing](../windows/boxing-cpp-component-extensions.md)
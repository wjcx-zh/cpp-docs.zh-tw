---
title: "範例容器類別 | Microsoft Docs"
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
  - "容器類別"
ms.assetid: 5b1451f2-c708-45da-bbf0-9e42fd687a1a
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 範例容器類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  本主題是 Visual c + + 文件為非功能性範例使用標準 c + + 程式庫中的容器中。 如需詳細資訊，請參閱 [STL 容器](../standard-library/stl-containers.md)。  
  
 描述控制不同長度的項目序列，通常是型別物件 **Ty**。 序列會儲存在不同的方式，根據實際的容器。  
  
 容器建構函式或成員函式可能會發現呼叫建構函式的情況下 **Ty**(**const Ty &**) 或函式 **Ty::operator =**(**const 置入 （& s)**)。 如果這類呼叫會擲回例外狀況，以便維持其完整性，並在它會攔截任何例外狀況重新擲回，被感謝容器物件。 您可以安全地交換，將指派來清除，或終結容器物件之後就會擲回這些例外狀況的其中一個。 一般而言，不過，您無法否則預測容器物件所控制之序列的狀態。  
  
 一些其他注意事項︰  
  
-   如果運算式 **~ Ty** 擲回例外狀況，產生的容器物件的狀態是未定義。  
  
-   如果容器儲存配置器物件 *al*, ，和 *al* 擲回例外狀況以外由於呼叫 *al***.allocate**, ，產生的容器物件的狀態會是未定義。  
  
-   如果容器儲存函式物件 *comp*, ，以決定如何排序受控制的序列，並 *comp* 擲回任何種類的例外狀況，產生的容器物件的狀態是未定義。  
  
 定義的 STL 容器類別符合幾個額外的需求，如下列段落中所述。  
  
 容器範本類別 [清單](../standard-library/list-class.md) 提供具決定性，且很有用，即使發生例外狀況，上述的行為。 比方說，如果在其中插入期間擲回例外狀況或多個項目，容器會保持不變，並重新擲回例外狀況。  
  
 如 *所有* 如果下列成員函式呼叫期間擲回例外狀況，STL、 所定義的容器類別︰  
  
```  
<A NAME="vclrfcontainerinsert"></A>insert // single element inserted  
<A NAME="vclrfcontainerpushback"></A>push_back  
<A NAME="vclrfcontainerpushfront"></A>push_front  
```  
  
 容器會保持不變，並重新擲回例外狀況。  
  
 如 *所有* 定義的 STL 容器類別，在下列成員函式呼叫的期間，回任何例外狀況︰  
  
```  
<A NAME="vclrfcontainerpopback"></A>pop_back  
<A NAME="vclrfcontainerpopfront"></A>pop_front  
```  
  
 成員函式 [清除](../standard-library/container-class-erase.md) （指派或複製建構） 的複製作業會擲回例外狀況時，才會發生例外狀況。  
  
 此外，任何例外狀況會擲不回時複製的成員函式所傳回的迭代器。  
  
 成員函式 [交換](../standard-library/container-class-swap.md) 讓其他承諾 *所有* 定義的 STL 容器類別︰  
  
-   只有當容器儲存配置器物件 al，成員函式擲回例外狀況和 `al` 會複製時，發生例外狀況。  
  
-   參考、 指標和迭代器，以指定在交換受控制序列的項目保持有效。  
  
 定義 STL 容器類別的物件配置並釋放它透過預存物件的型別所控制序列的儲存體 `Alloc`, ，這通常是範本參數。 這種配置器物件必須具有相同的外部介面的類別物件 **配置器 \< Ty>**。 特別是， `Alloc` 必須是相同的型別 **Alloc::rebind \< value_type >:: 其他**  
  
 如 *所有* STL、 成員函式所定義的容器類別 **配置 get_allocator const;** 傳回預存配置器物件的複本。 請注意，預存配置器物件是 *不* 複製已指定容器物件。 所有建構函式初始化值儲存在 **配置器**, 至 `Alloc` 如果建構函式包含配置器的參數。  
  
 根據 c + + 標準，定義 STL 容器類別可能會假設︰  
  
-   類別的所有物件 `Alloc` 比較等。  
  
-   型別 **Alloc::const_pointer** 相同 **const Ty \***。  
  
-   型別 **Alloc::const_reference** 相同 **const Ty &**。  
  
-   型別 **Alloc::pointer** 相同 **Ty \***。  
  
-   型別 **Alloc::reference** 相同 **Ty &**。  
  
 不過，在此實作中，容器不會進行這種簡化的假設。 因此，它們能夠正常運作是比較遠大的配置器物件︰  
  
-   類別的所有物件 `Alloc` 不需要比較相等。 （您可以維護多個集區的儲存體）。  
  
-   型別 **Alloc::const_pointer** 不需要相同 **const Ty \***。 （const 指標可以是類別）。  
  
-   型別 **Alloc::pointer** 不需要相同 **Ty \***。 （指標可以是類別）。  
  
## <a name="requirements"></a>需求  
 **標頭**: \< 範例容器>  
  
## <a name="see-also"></a>另請參閱  
 [\< 範例容器>](../standard-library/sample-container.md)


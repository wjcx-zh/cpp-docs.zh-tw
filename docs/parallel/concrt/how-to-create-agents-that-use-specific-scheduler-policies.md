---
title: 如何： 建立使用特定排程器原則的代理程式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- scheduler policies, agents [Concurrency Runtime]
- creating agents that use specific policies [Concurrency Runtime]
ms.assetid: 46a3e265-0777-4ec3-a142-967bafc49d67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9efa40d24ed4eaee5b9fd3995a4cf9ed696eb39a
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33685732"
---
# <a name="how-to-create-agents-that-use-specific-scheduler-policies"></a>如何：建立使用特定排程器原則的代理程式
代理程式是以非同步方式運作，與其他元件可解決較大型的運算工作的應用程式元件。 代理程式通常具有設定的生命週期，並維護狀態。  
  
 每個代理程式可能都有唯一的應用程式需求。 例如，代理程式，可讓使用者互動 （擷取輸入或顯示輸出） 可能需要較高的優先順序存取運算資源。 排程器原則可讓您控制的排程器在管理工作時使用的策略。 本主題示範如何建立使用特定排程器原則的代理程式。  
  
 如需使用自訂的排程器原則，以及非同步訊息區的基本範例，請參閱[How to： 指定特定排程器原則](../../parallel/concrt/how-to-specify-specific-scheduler-policies.md)。  
  
 本主題會使用非同步代理程式庫，例如代理程式、 訊息區塊和訊息傳遞函式，從執行工作的功能。 如需有關非同步代理程式程式庫的詳細資訊，請參閱[非同步代理程式程式庫](../../parallel/concrt/asynchronous-agents-library.md)。  
  
## <a name="example"></a>範例  
 下列範例會定義兩個類別衍生自[concurrency:: agent](../../parallel/concrt/reference/agent-class.md):`permutor`和`printer`。 `permutor`類別計算給定的輸入字串的所有排列。 `printer`類別列印進度訊息給主控台。 `permutor`類別執行密集運算，這可能會使用所有可用的運算資源。 若要發揮作用，`printer`類別必須及時列印每個進度訊息。  
  
 若要提供`printer`類別公平運算資源的存取，此範例會使用所述的步驟[如何： 管理排程器執行個體](../../parallel/concrt/how-to-manage-a-scheduler-instance.md)建立的自訂原則的排程器執行個體。 自訂原則指定的執行緒優先順序最高的優先權類別。  
  
 為了說明使用的自訂原則的排程器的優點，此範例會執行整體工作兩次。 範例一開始會使用預設排程器排程這兩項工作。 然後此範例使用預設排程器排程`permutor`物件和已排程的自訂原則的排程器`printer`物件。  
  
 [!code-cpp[concrt-permute-strings#1](../../parallel/concrt/codesnippet/cpp/how-to-create-agents-that-use-specific-scheduler-policies_1.cpp)]  
  
 此範例會產生下列輸出。  
  
```Output  
With default scheduler:  
Computing all permutations of 'Grapefruit'...  
100% complete...  
 
With higher context priority:  
Computing all permutations of 'Grapefruit'...  
100% complete...  
```  
  
 雖然這兩組工作會產生相同的結果，會使用自訂原則的版本可讓`printer`在更高的優先權執行，使其更 responsively 行為的物件。  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 範例程式碼複製並將它貼入 Visual Studio 專案中，或將它貼入名為的檔案中`permute-strings.cpp`，然後在 Visual Studio 命令提示字元視窗中執行下列命令。  
  
 **cl.exe /EHsc permute-strings.cpp**  
  
## <a name="see-also"></a>另請參閱  
 [排程器原則](../../parallel/concrt/scheduler-policies.md)   
 [非同步代理程式](../../parallel/concrt/asynchronous-agents.md)   
 


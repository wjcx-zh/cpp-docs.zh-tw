---
title: 1.4 相容性 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 662ad260-b9a1-43b7-b269-ef6ff0714e05
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c1bde41491f456ff99b0cd0d1ccc8ab98508412
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="14-compliance"></a>1.4 符合標準
OpenMP C/c + + 應用程式開發介面的實作是*OpenMP 相容*如果辨識，並會保留此規格中，所有項目的語意章節 1、 2、 3、 4 中所配置和附錄 c 附錄 A、 B、 D、 E 和 F 的資訊之用，而且不規格的一部分。 包含的 API 子集的實作不 OpenMP 標準。  
  
 OpenMP C 和 c + + 應用程式開發介面是基底實作所支援的語言擴充功能。 如果基底語言不支援的語言建構或所顯示延伸模組這份文件中，OpenMP 實作不是必要的支援。  
  
 所有標準的 C 和 c + + 程式庫函式和內建函式 （也就是函式的編譯器有特定的知識） 必須是安全執行緒。 未同步處理的使用由不同的執行緒在平行區域內的安全執行緒的函式不會產生未定義的行為。 不過，行為可能不在序列的區域相同。 （隨機的數字產生函數是一個範例）。  
  
 OpenMP C/c + + 應用程式開發介面可讓您指定特定行為是*實作定義。* 定義並在這些情況下，其行為的文件需要合格的 OpenMP 實作。 請參閱[附錄 E](../../parallel/openmp/e-implementation-defined-behaviors-in-openmp-c-cpp.md)，頁面 97，實作定義行為的清單。
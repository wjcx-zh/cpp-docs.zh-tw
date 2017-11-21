---
title: "運算式評估工具錯誤 CXX0030 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0030
dev_langs: C++
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ffa1dd85419943ede6a13d61cb82924c32b5e80a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="expression-evaluator-error-cxx0030"></a>運算式評估工具錯誤 CXX0030
無法評估運算式  
  
 當寫入偵錯工具的運算式評估工具無法取得運算式的值。 一個可能的原因是運算式參考外部程式的位址空間的記憶體 （取值 null 指標是一個範例）。 Windows 不允許存取外部程式的位址空間的記憶體。  
  
 您可以重新撰寫運算式，利用括號控制的評估順序。  
  
 這個錯誤是與 can0030 相同。
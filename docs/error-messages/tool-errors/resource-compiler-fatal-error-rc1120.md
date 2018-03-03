---
title: "資源編譯器嚴重錯誤 RC1120 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC1120
dev_langs:
- C++
helpviewer_keywords:
- RC1120
ms.assetid: 4e462931-e42e-42e3-8bfc-847677194286
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28a35cc2f932cdf655324d05c10bdb875aa895a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1120"></a>資源編譯器嚴重錯誤 RC1120
記憶體不足，請需要位元組數  
  
 資源編譯器已用完存放裝置，它會儲存其堆積中的項目。 這通常是有太多符號。  
  
### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正  
  
1.  增加 Windows 交換檔空間。 如需有關如何增加分頁檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體。  
  
2.  排除不必要包含檔案，特別是不必要的`#define`s 和函式原型。  
  
3.  目前的檔案分割成兩個或多個檔案，然後分別進行編譯。  
  
4.  移除其他程式或系統，可能會消耗大量的記憶體中執行的驅動程式。
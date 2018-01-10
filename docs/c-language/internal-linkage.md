---
title: "內部連結 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- internal linkage
- linkage [C++], internal
ms.assetid: 80be7b51-c930-43db-94d6-4f09a64077bf
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e6ca8a9e9804aa6c14077b023d0014062067f324
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="internal-linkage"></a>內部連結
如果某物件或函式的檔案範圍識別項宣告包含 *storage-class-specifier* **static**，則該識別項具有內部連結。 否則，該識別項會具有外部連結。 如需 [storage-class-specifier](../c-language/c-storage-classes.md) 非終端項的討論，請參閱*儲存類別*。  
  
 在一個轉譯單位中，具有內部連結之識別項的每個執行個體表示相同的識別項或函式。 內部連結的識別項在轉譯單位中是唯一的。  
  
## <a name="see-also"></a>請參閱  
 [使用 extern 指定連結](../cpp/using-extern-to-specify-linkage.md)
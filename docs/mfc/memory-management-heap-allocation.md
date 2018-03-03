---
title: "記憶體管理： 堆積配置 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- memory [MFC], detecting leaks
- delete operator [MFC], using with debug MFC
- heap allocation [MFC], described
- memory allocation [MFC], heap memory
- memory leaks [MFC], detecting
- new operator [MFC], using with debug MFC
- heap allocation [MFC]
- detecting memory leaks [MFC]
ms.assetid: a5d949c6-1b79-476e-9c66-513a558203d9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 34fbb82a28c145ad2d376f0647fbd75faeb9401c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="memory-management-heap-allocation"></a>記憶體管理：堆積配置
堆積可為程式保留所需的記憶體配置。 這是屬於程式碼和堆疊以外的區域。 典型的 C 程式使用函式`malloc`和**可用**配置及取消配置堆積記憶體。 MFC 的偵錯版本提供修改的過的 c + + 內建運算子**新**和**刪除**配置及取消配置堆積記憶體中的物件。  
  
 當您使用**新**和**刪除**而不是`malloc`和**可用**，您便能夠利用類別庫的記憶體管理偵錯增強功能它可以是用於偵測記憶體流失問題。 當您建置您的程式與 MFC 的標準版本的發行版本**新**和**刪除**運算子提供有效率的方式來配置及取消配置記憶體 （MFC 發行版本不提供這些運算子的修改的版本）。  
  
 請注意，堆積上配置物件的總大小受限於您系統上可用的虛擬記憶體大小。  
  
## <a name="see-also"></a>請參閱  
 [記憶體管理](../mfc/memory-management.md)


---
title: 記憶體管理： 堆積配置 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d7ef166201103b1544d0a36d82452b485af75418
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928605"
---
# <a name="memory-management-heap-allocation"></a>記憶體管理：堆積配置
堆積可為程式保留所需的記憶體配置。 這是屬於程式碼和堆疊以外的區域。 典型的 C 程式使用函式**malloc**和**可用**配置及取消配置堆積記憶體。 MFC 的偵錯版本提供修改的過的 c + + 內建運算子**新**和**刪除**配置及取消配置堆積記憶體中的物件。  
  
 當您使用**新**和**刪除**而不是**malloc**和**可用**，您便能夠利用類別庫記憶體管理偵錯增強功能，可用於偵測記憶體流失問題。 當您建置您的程式與 MFC 的標準版本的發行版本**新**和**刪除**運算子提供有效率的方式來配置及取消配置記憶體 （MFC 發行版本不提供這些運算子的修改的版本）。  
  
 請注意，堆積上配置物件的總大小受限於您系統上可用的虛擬記憶體大小。  
  
## <a name="see-also"></a>另請參閱  
 [記憶體管理](../mfc/memory-management.md)


---
title: 記憶體管理：堆積配置
ms.date: 11/04/2016
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
ms.openlocfilehash: 0c669fa611193b9a04e4854c84dec604e585991c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50641151"
---
# <a name="memory-management-heap-allocation"></a>記憶體管理：堆積配置

堆積可為程式保留所需的記憶體配置。 這是屬於程式碼和堆疊以外的區域。 典型的 C 程式使用函式**malloc**並**免費**配置及取消配置堆積記憶體。 MFC 的偵錯版本提供修改的過的 c + + 內建運算子**新**並**刪除**配置及取消配置堆積記憶體中的物件。

當您使用**新**並**刪除**而不是**malloc**並**免費**，就能夠利用類別庫記憶體管理偵錯增強功能，可用於偵測記憶體流失。 當您建置您的程式與 MFC 的標準版本的發行版本**新**並**刪除**運算子提供有效的方式來配置及取消配置記憶體 （MFC 發行版本不提供這些運算子的修改的版本）。

請注意，堆積上配置物件的總大小受限於您系統上可用的虛擬記憶體大小。

## <a name="see-also"></a>另請參閱

[記憶體管理](../mfc/memory-management.md)


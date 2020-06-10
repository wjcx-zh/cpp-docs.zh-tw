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
ms.openlocfilehash: 1f0b07a0a3439faba71078af1e2d7d1559a42b41
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626287"
---
# <a name="memory-management-heap-allocation"></a>記憶體管理：堆積配置

堆積可為程式保留所需的記憶體配置。 這是屬於程式碼和堆疊以外的區域。 一般 C 程式會使用**malloc**和**free**函數來配置和解除配置堆積記憶體。 MFC 的 Debug 版本提供修改過的 c + + 內建運算子**new**和**delete**版本，以配置和解除配置堆積記憶體中的物件。

當您使用**new**和**delete**而不是**malloc**和**free**時，您可以利用類別庫的記憶體管理偵錯工具增強功能，這有助於偵測記憶體流失。 當您使用 MFC 的發行版本建立程式時，**新**的和**delete**運算子的標準版本可提供有效率的方式來配置和解除配置記憶體（MFC 的發行版本不會提供這些運算子的修改版本）。

請注意，堆積上配置物件的總大小受限於您系統上可用的虛擬記憶體大小。

## <a name="see-also"></a>另請參閱

[記憶體管理](memory-management.md)

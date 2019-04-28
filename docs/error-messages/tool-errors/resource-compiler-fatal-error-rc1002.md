---
title: 資源編譯器嚴重錯誤 RC1002
ms.date: 11/04/2016
f1_keywords:
- RC1002
helpviewer_keywords:
- RC1002
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
ms.openlocfilehash: 0804e7db92355c023e4f9f1dbef8d9194caa3718
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297732"
---
# <a name="resource-compiler-fatal-error-rc1002"></a>資源編譯器嚴重錯誤 RC1002

堆積空間不足

### <a name="to-fix-by-using-the-following-possible-solutions"></a>使用下列可能的解決方式來進行修正

1. 增加 Windows 分頁檔空間。 如需有關如何增加分頁檔空間的詳細資訊，請參閱 Windows 說明中的虛擬記憶體。

1. 目前的檔案分割成較小的檔案，然後分別進行編譯。

1. 移除其他程式或系統上執行的驅動程式。
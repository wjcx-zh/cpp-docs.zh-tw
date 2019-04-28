---
title: 封送處理
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 0661a4cdde0a3a875cf27221e884f6c65b9fea55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262381"
---
# <a name="marshaling"></a>封送處理

封送處理 COM 技術可讓用於另一個處理序的其中一個處理序中的物件所公開的介面。 在封送處理 COM 提供的程式碼 （或使用介面的實作項所提供的程式碼） 來封裝方法之參數的格式可移動的跨處理序 （以及，透過網路在其他電腦上執行的程序），並解壓縮這些參數另一端。 同樣地，COM 也必須執行以上相同步驟，在從呼叫傳回。

> [!NOTE]
>  封送處理通常是不必要的物件相同的程序中使用由物件所提供的介面時。 不過，封送處理可能需要在執行緒之間。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[封送處理的詳細資料](/windows/desktop/com/marshaling-details)

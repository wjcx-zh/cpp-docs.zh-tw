---
title: 封送處理
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 9963e261f26daa57cb58e30ffc404b431d781bfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492047"
---
# <a name="marshaling"></a>封送處理

封送處理的 COM 技術可讓某個進程中的物件所公開的介面, 在另一個進程中使用。 在封送處理中, COM 會提供程式碼 (或使用介面實作項所提供的程式碼), 將方法的參數封裝成可跨進程移動的格式 (以及跨網路到其他電腦上執行的處理常式), 並將這些參數解除包裝。另一端。 同樣地, COM 必須執行從呼叫傳回的相同步驟。

> [!NOTE]
>  當物件提供的介面與物件在相同進程中使用時, 通常不需要封送處理。 不過, 執行緒之間可能需要封送處理。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[封送處理詳細資料](/windows/win32/com/marshaling-details)

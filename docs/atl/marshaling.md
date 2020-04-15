---
title: 封送處理
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling, COM interop
- marshaling
- COM interfaces, marshaling
ms.assetid: 40644b0a-1106-4fc8-9dfb-9bee9915d825
ms.openlocfilehash: 83cf29fb45347b7bfcfc1644546684f074061d25
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319345"
---
# <a name="marshaling"></a>封送處理

COM 封送技術允許在一個進程中由物件公開的介面在另一個進程中使用。 在封送中,COM 提供代碼(或使用介面實現器提供的代碼),既將方法的參數打包成一種可以跨進程行動的格式(以及跨線移動到其他電腦上運行的進程),又在另一端解壓縮這些參數。 同樣,COM 必須在從呼叫返回時執行這些相同的步驟。

> [!NOTE]
> 當物件提供的介面與物件在同一進程中使用時,通常不需要封送。 但是,線程之間可能需要封送。

## <a name="see-also"></a>另請參閱

[COM 簡介](../atl/introduction-to-com.md)<br/>
[封送詳細資訊](/windows/win32/com/marshaling-details)

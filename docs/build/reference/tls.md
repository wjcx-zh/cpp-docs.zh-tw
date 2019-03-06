---
title: /TLS
ms.date: 11/04/2016
f1_keywords:
- /TLS
helpviewer_keywords:
- /TLS dumpbin option
- -TLS dumpbin option
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
ms.openlocfilehash: 1760e94046a950f67d3c3fd7ef13aa40ca7de47a
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57417784"
---
# <a name="tls"></a>/TLS

顯示 IMAGE_TLS_DIRECTORY 結構從可執行檔。

## <a name="remarks"></a>備註

/ TLS 結構的欄位以及 TLS 回呼函式的位址，則會顯示 TLS。

如果程式不會使用執行緒區域儲存區，其映像不會包含 TLS 結構。  請參閱[執行緒](../../cpp/thread.md)如需詳細資訊。

IMAGE_TLS_DIRECTORY winnt.h 中定義。

## <a name="see-also"></a>另請參閱

[DUMPBIN 選項](../../build/reference/dumpbin-options.md)

---
title: 什麼是資料流 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- reading data [C++], iostream programming
- data [C++], reading
- streams [C++], in iostream classes
- streams [C++]
ms.assetid: a7e661e9-6cd1-4543-a9a4-c58ee9fd32f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47f56a3d717c2dc9cebb3df30739954e5f6bf9e1
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853735"
---
# <a name="what-a-stream-is"></a>什麼是資料流

如同 C，C++ 不具內建的輸入/輸出功能。 不過，所有的 C++ 編譯器都會搭配一個系統化的物件導向 I/O 封裝 (稱為 iostream 類別)。 資料流是 iostream 類別的中心概念。 您可以將資料流物件視為智慧型檔案，以做為位元組的來源和目的地。 資料流的特性取決於它的類別及自訂的插入和擷取運算子。

透過裝置驅動程式，磁碟作業系統就能將鍵盤、螢幕、印表機及通訊埠當成延伸的檔案來處理。 iostream 類別會與這些延伸的檔案進行互動。 內建類別所支援的讀取和寫入記憶體的語法與磁碟 I/O 的語法完全相同，以便輕鬆地衍生資料流類別。

## <a name="in-this-section"></a>本節內容

[輸入/輸出替代項目](../standard-library/input-output-alternatives.md)

## <a name="see-also"></a>另請參閱

[iostream 程式設計](../standard-library/iostream-programming.md)<br/>

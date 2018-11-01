---
title: 2.4 工作共用的建構
ms.date: 11/04/2016
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
ms.openlocfilehash: e7bf8d37ecdc6a3ef451c9d9746fb47a76a16eb4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50502878"
---
# <a name="24-work-sharing-constructs"></a>2.4 工作共用的建構

工作共用建構會將執行相關聯的陳述式，會遇到相同的小組成員之間。 工作共用指示詞不會啟動新的執行緒，並在工作共用建構的項目上沒有任何隱含的障礙。

將一連串工作共用建構並**屏障**遇到的指示詞必須是相同的小組中的每個執行緒。

OpenMP 定義下列的工作共用建構，並說明下列各節：

- **針對**指示詞

- **區段**指示詞

- **單一**指示詞
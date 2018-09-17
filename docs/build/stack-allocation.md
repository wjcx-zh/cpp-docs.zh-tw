---
title: 堆疊配置 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098e51f2-eda6-40d0-b149-0b618aa48b47
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0210239f2d915fcc3445a74cfdf5b0d1796df7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701495"
---
# <a name="stack-allocation"></a>堆疊配置

函式的初構會負責配置堆疊空間的本機變數，儲存的暫存器，堆疊參數和暫存器參數。

是一律，[參數] 區域底部的堆疊 （即使使用 alloca），如此一來，它一律是相鄰的傳回位址的任何函式呼叫期間。 它包含至少四個項目，但一定足夠空間來保存所有的參數所需的任何可能被呼叫的函式。 請注意，即使參數本身會在堆疊; 永遠不會主目錄，暫存器參數一律配置空間被呼叫端會保證其所有的參數有已配置空間。 住家地址所需的暫存器引數的因此如果呼叫的函式需要的引數清單 (va_list) 或個別引數位址的連續區域使用。 此區域也提供方便的地方來儲存暫存器引數，thunk 執行期間，或做為偵錯的選項 （例如，它很容易引數如果它們儲存在其初構程式碼中的住家地址，偵錯期間尋找）。 即使呼叫的函式具有少於 4 個參數，這 4 的堆疊位置有效地呼叫的函式，所擁有，並可能由所呼叫函式用於儲存暫存器值的參數以外的其他用途。  因此呼叫者可能不會儲存資訊在堆疊的這個區域中跨函式呼叫。

如果以動態方式配置空間 (alloca) 函式，靜態暫存器必須用作框架指標來標記的固定部分堆疊的基底，然後該暫存器必須儲存以初始化初構中。 請注意，使用 alloca 時，從相同的呼叫端呼叫相同的被呼叫端可能會有不同的住家地址為暫存器參數。

堆疊一律會維持 16 個位元組對齊，除非內 （例如之後會推入的傳回位址,），初構和 try-except 中指示的位置[函式型別](../build/function-types.md)框架函式的特定類別。

以下是所有暫存器和堆疊所需的參數在堆疊底部的 B 中 where 函式的呼叫非分葉函式 b 函式 A 的初構堆疊配置的範例有已配置空間。 呼叫會推入的傳回位址和 B 的初構會針對其本機變數、 靜態暫存器，並呼叫函式所需的空間配置空間。 如果 B 使用 alloca，則會儲存區域的本機變數/靜態暫存器和參數堆疊區域之間配置的空間。

![AMD 轉換範例](../build/media/vcamd_conv_ex_5.png "AMD 轉換範例")

當函式 B 呼叫另一個函式時，為住家地址的正下方 RCX 的推入的傳回位址。

## <a name="see-also"></a>另請參閱

[堆疊使用方式](../build/stack-usage.md)
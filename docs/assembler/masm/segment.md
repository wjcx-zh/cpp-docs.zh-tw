---
title: 區段 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- SEGMENT
dev_langs:
- C++
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c55416cc5a757128c9cc97b2f342953911ac2946
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
ms.locfileid: "32058107"
---
# <a name="segment"></a>SEGMENT
定義程式區段，稱為*名稱*區段屬性  
  
## <a name="syntax"></a>語法  
  
```  
  
   name SEGMENT [[READONLY]] [[align]] [[combine]] [[use]] [[characteristics]] ALIAS(string) [['class']]  
statements  
name ENDS  
```  
  
#### <a name="parameters"></a>參數  
 *align*  
 可以從中選取的區段的起始位址的記憶體位址範圍。 對齊類型可以是下列其中一項動作：  
  
|對齊類型|起始位址|  
|----------------|----------------------|  
|**BYTE**|下一個可用的位元組位址。|  
|**WORD**|下一個可用的字位址 （每個字的 2 位元組）。|  
|**DWORD**|下一個可用的雙字組位址 （每個雙字組 4 個位元組）。|  
|**PARA**|下一個可用的段落位址 （每個段落的 16 位元組）。|  
|**PAGE**|下一個可用的頁面位址 （每一頁的 256 個位元組）。|  
|**對齊**(*n*)|下一個可用*n*個位元組的位址。 如需詳細資訊，請參閱 < 備註 > 一節。|  
  
 如果未指定這個參數， **PARA**預設會使用。  
  
 *combine*  
 **公用**，**堆疊**，**常見**，**記憶體**，**在 * * * 位址*，**私用**  
  
 *use*  
 **USE16**， **USE32**，**一般**  
  
 `characteristics`  
 **資訊**，**讀取**，**寫入**， **EXECUTE**，**共用**， **NOPAGE**， **NOCACHE**，和**捨棄**  
  
 這些只支援 COFF，而對應至名稱類似的 COFF 區段特性 (例如，**共用**對應至 IMAGE_SCN_MEM_SHARED)。 讀取設定 IMAGE_SCN_MEM_READ 旗標。 過時的唯讀旗標會引起清除 IMG_SCN_MEM_WRITE 旗標 > 一節。 如果有任何`characteristics`設定，不會使用預設特性，而且只有程式設計人員指定旗標作用中。  
  
 `ALIAS(` `string` `)`  
 這個字串會作為發出 COFF 物件中的區段名稱。  建立多個區段具有相同的外部名稱，以不同的 MASM 區段名稱。  
  
 不支援與 **/omf**。  
  
 `class`  
 指定應該如何結合並排序組合檔案中區段。 典型值為， `'DATA'`， `'CODE'`，`'CONST'`和 `'STACK'`  
  
## <a name="remarks"></a>備註  
 如`ALIGN(n)`，`n`可能是任何 2 的乘冪從 1 到 8192; 不支援 **/omf**。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞參考](../../assembler/masm/directives-reference.md)
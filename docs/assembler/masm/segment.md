---
title: SEGMENT
ms.date: 12/06/2019
f1_keywords:
- SEGMENT
helpviewer_keywords:
- SEGMENT directive
ms.assetid: e6f68367-6714-4f06-a79c-edfa88014430
ms.openlocfilehash: 933e4e42b4b0f9cc979a3e67805d017f723472ef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988009"
---
# <a name="segment"></a>SEGMENT

定義名為*name*且含有區段屬性的程式區段

## <a name="syntax"></a>語法

> *名稱***區段**⟦**READONLY**⟧⟦*align*⟧⟦*結合*⟧⟦*use*⟧⟦*特性*⟧ **ALIAS （** _string_ **）** ⟦ __'__ *class* __'__ ⟧ \
> *語句*\
> *名稱***結束**

#### <a name="parameters"></a>參數

*align*<br/>
可從中選取區段之起始位址的記憶體位址範圍。 對齊類型可以是下列任何一項：

|對齊類型|起始位址|
|----------------|----------------------|
|**BYTE**|下一個可用的位元組位址。|
|**WORD**|下一個可用的文字位址（每個字2個位元組）。|
|**DWORD**|下一個可用的雙字組位址（每個雙單字4個位元組）。|
|**並行**|下一個可用的段落位址（每個段落16個位元組）。|
|**PAGE**|下一個可用的頁面位址（每頁256個位元組）。|
|**對齊**（*n*）|下一個可用的第*n*個位元組位址。 如需詳細資訊，請參閱備註一節。|

如果未指定此參數，則預設會使用 [**段落**]。

*合併*（僅限32位 MASM） \
**公用**，**堆疊**，**一般**，**記憶體**，<em>位址</em>，**私**用

*使用*（僅限32位 MASM） \
**USE16**、 **USE32**、**平直**

*特性*\
**INFO**、 **READ**、 **WRITE**、 **EXECUTE**、 **SHARED**、 **NOPAGE**、 **NOCACHE**和**捨棄**

這些僅支援 COFF，並對應至類似名稱的 COFF 區段特性（例如， **SHARED**對應至 IMAGE_SCN_MEM_SHARED）。 [讀取] 會設定 IMAGE_SCN_MEM_READ 旗標。 過時的 READONLY 旗標會導致區段清除 IMG_SCN_MEM_WRITE 旗標。 如果設定了任何*特性*，則不會使用預設特性，而且只有程式設計人員指定的旗標才會生效。

_string_\
這個字串會當做發出的 COFF 物件中的區段名稱使用。  使用不同的 MASM 區段名稱，建立具有相同外部名稱的多個區段。

不支援 **/omf**。

*class*\
指定如何在組合的檔案中合併和排序區段。 一般的值為、`'DATA'`、`'CODE'`、`'CONST'` 和 `'STACK'`

## <a name="remarks"></a>備註

針對 `ALIGN(n)`， *n*可能是從1到8192的2乘冪;不支援 **/omf**。

## <a name="see-also"></a>請參閱

[指示詞參考](directives-reference.md)

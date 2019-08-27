---
title: 針對 BSTR 配置及釋放記憶體
ms.date: 11/04/2016
f1_keywords:
- bstr
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
ms.openlocfilehash: a7a82acff959d18dcadd3a2c8516a20d60a617d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491405"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>針對 BSTR 配置及釋放記憶體

當您建立`BSTR`並在 COM 物件之間傳遞時, 您必須負責處理它們所使用的記憶體, 以避免記憶體流失。 `BSTR`當維持在介面中時, 您必須在完成時釋放其記憶體。 不過, 當`BSTR`傳入介面時, 接收物件會負責其記憶體管理。

一般來說, 配置和釋放配置給的`BSTR`記憶體的規則如下:

- 當您呼叫需要`BSTR`引數的函式時, 您必須在呼叫`BSTR`之前配置的記憶體, 並于之後釋放它。 例如：

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- 當您呼叫會傳回的`BSTR`函式時, 您必須自行釋放字串。 例如：

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- 當您執行會傳回的`BSTR`函式時, 請配置字串但不要釋放它。 接收函數會釋放記憶體。 例如：

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>另請參閱

[字串 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)

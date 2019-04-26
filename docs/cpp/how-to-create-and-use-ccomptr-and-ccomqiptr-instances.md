---
title: HOW TO：建立和使用 CComPtr 和 CComQIPtr 執行個體
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 2bcabfe80185939b899c84fc44f71b98608fc3c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154057"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>HOW TO：建立和使用 CComPtr 和 CComQIPtr 執行個體

在傳統的 Windows 程式設計，程式庫通常是實作為 COM 物件 (或更精確地說是 COM 伺服器)。 許多 Windows 作業系統元件都會實作為 COM 伺服器，而且許多參與者提供這種形式的程式庫。 如需 COM 基本概念的資訊，請參閱 [Component Object Model (COM)](/windows/desktop/com/component-object-model--com--portal)。

當您具現化元件物件模型 (COM) 物件時，請將介面指標存放於 COM 智慧型指標，它在解構函式中使用 `AddRef` 和 `Release` 呼叫來執行參考計數。 如果您使用 Active Template Library (ATL) 或 MFC 程式庫，則使用 `CComPtr` 智慧型指標。 如果您不使用 ATL 或 MFC，則使用 `_com_ptr_t`。 由於沒有 `std::unique_ptr`的 COM 對等用法，為單一擁有者和多擁有者案例中使用這些智慧型指標。 `CComPtr` 和 `ComQIPtr` 都支援有右值參考的移動作業。

## <a name="example"></a>範例

下列範例示範如何使用 `CComPtr` 以具現化 COM 物件和取得其介面的指標。 請注意 `CComPtr::CoCreateInstance` 成員函式用以建立 COM 物件，而不是有相同名稱的 Win32 函式。

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` 和其相關是 ATL 的一部分，且會定義在\<atlcomcli.h >。 `_com_ptr_t` 宣告於\<comip.h >。 當編譯器產生類型程式庫的包裝函式類別時，編譯器會建立 `_com_ptr_t` 的特製化。

## <a name="example"></a>範例

ATL 也提供 `CComQIPtr`，查詢 COM 物件以擷取其他介面的語法更簡單。 然而，建議使用 `CComPtr` ，因為 `CComQIPtr` 可以執行的所有作業，它也可以執行，而且在語意上與原始 COM 介面指標更加一致。 如果您使用 `CComPtr` 查詢介面，新介面指標是放在 out 參數中。 如果呼叫失敗，傳回 HRESULT，這是一般的 COM 模式。 使用 `CComQIPtr`，傳回值是指標本身，而且如果呼叫失敗，無法存取內部 HRESULT 傳回值。 下列兩行顯示 `CComPtr` 和 `CComQIPtr` 的錯誤處理機制之間的差異。

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>範例

`CComPtr` 提供 IDispatch 特製化，讓它能夠儲存 COM Automation 元件指標並藉由使用晚期繫結叫用方法。 `CComDispatchDriver` 是 `CComQIPtr<IDispatch, &IIDIDispatch>`的 typedef，它可以隱含地轉換為 `CComPtr<IDispatch>`。 因此，當任何這三個名稱出現在程式碼中，它相當於 `CComPtr<IDispatch>`。 下列範例顯示如何使用 `CComPtr<IDispatch>`，取得 Microsoft Word 物件模型的指標。

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>另請參閱

[智慧型指標 (現代 C++)](../cpp/smart-pointers-modern-cpp.md)

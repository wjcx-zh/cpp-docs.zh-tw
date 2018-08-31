---
title: 委派 (C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3175bf1c-86d8-4eda-8d8f-c5b6753d8e38
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fda9cab73088746ec64caf482f9e606d713eaa4f
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43222739"
---
# <a name="delegates-ccx"></a>委派 (C++/CX)
`delegate`關鍵字用來宣告 Windows 執行階段相當於在 standard c + + 中的函式物件的參考型別。 委派宣告類似於函式簽章，會指定其包裝函式必須有的傳回類型和參數類型。 這是使用者定義的委派宣告：  
  
```cpp  
     public delegate void PrimeFoundHandler(int result);  
```  
  
 委派最常與事件搭配使用。 事件有委派類型，與類別可以有介面類型十分相似。 委派代表事件處理常式必須滿足的合約。 下列事件類別成員的類型是先前定義的委派：  
  
```cpp  
event PrimeFoundHandler^ primeFoundEvent;  
```  
  
 當宣告透過 Windows 執行階段應用程式二進位介面會公開的委派對用戶端，使用[Windows::Foundation::TypedEventHandler\<，TResult >](https://msdn.microsoft.com/library/windows/apps/br225997.aspx)。 此委派具有預先定義的 Proxy 與 Stub 二進位檔，使其能夠供 Javascript 用戶端使用。  
  
## <a name="consuming-delegates"></a>使用委派  
 當您建立通用 Windows 平台應用程式時，您通常使用做為 Windows 執行階段類別所公開的事件類型的委派。 若要訂閱事件，請指定符合委派簽章的函式 (Lambda)，建立事件的委派類型執行個體。 然後使用 `+=` 運算子，將委派物件傳遞給類別的事件成員。 這就是所謂的訂閱事件。 當類別執行個體「引發」事件時，就會呼叫您的函式，以及任何其他已由您的物件或其他物件加入的處理常式。  
  
> [!TIP]
>  當您建立事件處理常式時，Visual Studio 會為您執行許多工作。 例如，如果您在 XAML 標記中指定事件處理常式，工具提示隨即出現。 如果您選擇工具提示，Visual Studio 會自動建立事件處理常式方法，並將此方法關聯至發行類別上的事件。  
  
 下列範例示範基本模式。 `Windows::Foundation::TypedEventHandler` 是委派類型。 處理常式函式可以透過具名函式建立。  
  
 在 app.h 中：  
  
 [!code-cpp[cx_delegates#120](../cppcx/codesnippet/CPP/delegatesevents/class1.h#120)]  
  
 在 app.cpp 中：  
  
 [!code-cpp[cx_delegates#121](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#121)]  
  
> [!WARNING]
>  一般來說，如果是事件處理常式，最好使用具名函式而不是 Lambda，除非您十分小心避免循環參考。 具名函式會依弱式參考擷取 "this" 指標，而 Lambda 則是依強式參考來擷取，並且會建立循環參考。 如需詳細資訊，請參閱 <<c0> [ 弱式參考與中斷循環](../cppcx/weak-references-and-breaking-cycles-c-cx.md)。  
  
 依照慣例，由 Windows 執行階段所定義的事件處理常式委派名稱具有表單 * EventHandler — 例如，RoutedEventHandler、 SizeChangedEventHandler 或 SuspendingEventHandler。 同樣依照慣例，事件處理常式委派會有兩個參數，並傳回 void。 在沒有類型參數的委派中，第一個參數是 [Platform::Object^](../cppcx/platform-object-class.md)類型，它保存對傳送者的參考，傳送者是引發事件的物件。 您必須先轉換回原始類型，才能在事件處理常式方法中使用這個引數。 在具有類型參數的事件處理常式委派中，第一個類型參數指定傳送者的類型，而第二個參數則是 ref 類別的控制代碼，保存事件的相關資訊。 依照慣例，該類別名為\*EventArgs。 例如，RoutedEventHandler 委派具有類型為 RoutedEventArgs^ 的第二個參數，而 DragEventHander 具有類型為 DragEventArgs^ 的第二個參數。  
  
 依照慣例，會將包裝在非同步作業完成時執行之程式碼的委派命名為 *CompletedHandler。 這些委派會定義為類別的屬性，而非事件。 因此，您不是使用 `+=` 運算子訂閱這些委派，而是直接指派委派物件給屬性。  
  
> [!TIP]
>  C++ IntelliSense 不會顯示完整的委派簽章，因此無法協助您判斷 EventArgs 參數的特定類型。 若要尋找類型，請移至 [ **物件瀏覽器** ]，尋找委派的 `Invoke` 方法。  
  
## <a name="creating-custom-delegates"></a>建立自訂委派  
 您可以定義自己的委派，可定義事件處理常式，或讓消費者將自訂功能傳遞至您的 Windows 執行階段元件。 像其他任何 Windows 執行階段類型，公用委派無法宣告為泛型。  
  
### <a name="declaration"></a>宣告  
 委派的宣告類似於函式宣告，不同的是委派為類型。 通常是在命名空間範圍宣告委派，不過您也可以巢狀方式在類別宣告中加入委派宣告。 下列委派會封裝以 `ContactInfo^` 做為輸入並傳回 `Platform::String^`的所有函式。  
  
 [!code-cpp[cx_delegates#111](../cppcx/codesnippet/CPP/delegatesevents/class1.h#111)]  
  
 宣告委派類型後，您可以宣告該類型的類別成員，或是宣告採用該類型物件當做參數的方法。 方法或函式也可以傳回委派類型。 在下列範例中， `ToCustomString` 方法接受委派做為輸入參數。 這個方法可讓用戶端程式碼提供自訂函式，而此自訂函式可從 `ContactInfo` 物件的部分或全部公用屬性建構字串。  
  
 [!code-cpp[Cx_delegates#112](../cppcx/codesnippet/CPP/delegatesevents/class1.h#112)]  
  
> [!NOTE]
>  您使用"^"符號參考委派型別時，就如同您使用任何 Windows 執行階段參考類型。  
  
 事件宣告一律都有委派類型。 此範例示範典型的委派類型簽章，在 Windows 執行階段：  
  
 [!code-cpp[cx_delegates#122](../cppcx/codesnippet/CPP/delegatesevents/class1.h#122)]  
  
 `Click` 類別中的 `Windows:: UI::Xaml::Controls::Primitives::ButtonBase` 事件是 `RoutedEventHandler`類型。 如需詳細資訊，請參閱 [Events](../cppcx/events-c-cx.md)。  
  
 用戶端程式碼首先使用 `ref new` ，並提供與委派簽章相容的 Lambda 來建構委派執行個體，以及定義自訂行為。  
  
 [!code-cpp[Cx_delegates#113](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#113)]  
  
 接著呼叫成員函式，並傳遞委派。 假設 `ci` 是 `ContactInfo^` 執行個體，而 `textBlock` 是 XAML `TextBlock^`。  
  
 [!code-cpp[Cx_delegates#114](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#114)]  
  
 在下一個範例中，用戶端應用程式將自訂委派傳遞至執行中的每個項目對委派的 Windows 執行階段元件中的公用方法`Vector`:  
  
 [!code-cpp[Cx_delegates#118](../cppcx/codesnippet/CPP/clientapp/mainpage.xaml.cpp#118)]  
  
 [!code-cpp[Cx_delegates#119](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#119)]  
  
### <a name="construction"></a>建構  
 您可以從下列任何物件建構委派：  
  
-   Lambda  
  
-   靜態函式  
  
-   成員指標  
  
-   std::function  
  
 下列範例顯示如何從每一個上述物件建構委派。 不論用來建構委派的物件類型為何，委派的使用方式都相同。  
  
 [!code-cpp[Cx_delegates#115](../cppcx/codesnippet/CPP/delegatesevents/class1.cpp#115)]  
  
> [!WARNING]
>  如果您使用可擷取 "this" 指標的 Lambda，請務必使用 `-=` 運算子，明確地從事件中解除登錄，然後再結束 Lambda。 如需詳細資訊，請參閱[事件](../cppcx/events-c-cx.md)。  
  
### <a name="generic-delegates"></a>泛型委派  
 C++/CX 的泛型委派有類似於泛型類別宣告的限制。 它們不能宣告為公用。 您可以宣告私用或內部泛型委派，然後從 C++ 使用它，但是 .NET 或 JavaScript 用戶端無法使用它，因為它沒有發出至 .winmd 中繼資料。 這個範例宣告僅供 C++ 使用的泛型委派：  
  
 [!code-cpp[Cx_delegates#116](../cppcx/codesnippet/CPP/delegatesevents/class1.h#116)]  
  
 下一個範例在類別定義內部宣告委派的特製化執行個體：  
  
 [!code-cpp[Cx_delegates#117](../cppcx/codesnippet/CPP/delegatesevents/class1.h#117)]  
  
## <a name="delegates-and-threads"></a>委派和執行緒  
 委派就像函式物件，其中包含將在未來執行的程式碼。 如果建立並傳遞委派的程式碼，以及接受並執行委派的函式在相同執行緒上執行，事情就會很簡單。 如果該執行緒是 UI 執行緒，則委派可以直接操作使用者介面物件 (例如 XAML 控制項)。  
  
 如果用戶端應用程式載入之執行緒的 apartment 中執行，並提供委派給該元件的 Windows 執行階段元件，則預設委派會叫用直接在 STA 執行緒上。 大部分的 Windows 執行階段元件可以在 STA 或 MTA 中執行。  
  
 如果執行委派的程式碼在不同的執行緒上執行 (例如，在 concurrency::task 物件的內容中)，則您必須負責同步處理對共用資料的存取。 例如，如果您的委派包含對 Vector 的參考，而某個 XAML 控制項也參考相同 Vector，那麼您必須採取步驟，以避免當委派和 XAML 控制項同時嘗試存取 Vector 時，可能發生的死結或競爭情形。 您也必須注意不讓委派以傳址方式，擷取在叫用委派前可能就超出範圍的區域變數。  
  
 如果希望您建立的委派在其所建立的相同執行緒上回呼 (例如，假設您將委派傳遞給在 MTA Apartment 中執行的元件)，而且希望在與建立者相同的執行緒上叫用，那麼請使用採用第二個 `CallbackContext` 參數的委派建構函式多載。 請只在具有已登錄 Proxy/Stub 的委派上使用此多載，不是每個以 Windows.winmd 定義的委派都有登錄。  
  
 如果您熟悉 .NET 的事件處理常式，就會知道建議的作法是在引發之前建立事件的本機複本。 這可避免在叫用事件之前可能移除事件處理常式的競爭情形。 在 C++/CX 中不需要這樣做，因為在加入或移除事件處理常式時會建立新的處理常式清單。 由於在叫用事件之前 C++ 物件會遞增事件處理常式清單上的參考計數，因此所有處理常式保證都是有效。 不過，這也表示，如果移除耗用端執行緒的事件處理常式，當發行物件在其現在已過時的清單複本上操作時，該處理常式可能仍然會被叫用。 直到下一次引發事件時，發行物件才會得到更新清單。  
  
## <a name="see-also"></a>另請參閱  
 [型別系統](../cppcx/type-system-c-cx.md)   
 [Visual c + + 語言參考](../cppcx/visual-c-language-reference-c-cx.md)   
 [命名空間參考](../cppcx/namespaces-reference-c-cx.md)
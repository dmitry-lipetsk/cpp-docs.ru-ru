---
title: "Класс chi_squared_distribution | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- chi_squared_distribution
- std::chi_squared_distribution
- random/std::chi_squared_distribution
- std::chi_squared_distribution::reset
- random/std::chi_squared_distribution::reset
- std::chi_squared_distribution::n
- random/std::chi_squared_distribution::n
- std::chi_squared_distribution::param
- random/std::chi_squared_distribution::param
- std::chi_squared_distribution::min
- random/std::chi_squared_distribution::min
- std::chi_squared_distribution::max
- random/std::chi_squared_distribution::max
- std::chi_squared_distribution::operator()
- random/std::chi_squared_distribution::operator()
- std::chi_squared_distribution::param_type
- random/std::chi_squared_distribution::param_type
- std::chi_squared_distribution::param_type::n
- random/std::chi_squared_distribution::param_type::n
- std::chi_squared_distribution::param_type::operator==
- random/std::chi_squared_distribution::param_type::operator==
- std::chi_squared_distribution::param_type::operator!=
- random/std::chi_squared_distribution::param_type::operator!=
dev_langs:
- C++
helpviewer_keywords:
- chi_squared_distribution class
ms.assetid: 9b603fbe-cafd-4a92-b8c5-a434d60b8122
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c7f3b346bc8abeab0c6bd913fc0b554bef4ed208
ms.openlocfilehash: 5e60b73c22a7704f63f70ae2e6498fc6e47dde1e
ms.lasthandoff: 02/24/2017

---
# <a name="chisquareddistribution-class"></a>Класс chi_squared_distribution
Формирует распределение хи-квадрат.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
template<class RealType = double>  
class chi_squared_distribution {
public:    
    // types 
    typedef RealType result_type;    
    struct param_type;  

    // constructor and reset functions 
    explicit chi_squared_distribution(RealType n = 1);
    explicit chi_squared_distribution(const param_type& parm);
    void reset();  

    // generating functions 
    template <class URNG>  
    result_type operator()(URNG& gen);
    template <class URNG>
    result_type operator()(URNG& gen, const param_type& parm);
    
    // property functions 
    RealType n() const;
    param_type param() const;
    void param(const param_type& parm);
    result_type min() const;
    result_type max() const;
};
```  
#### <a name="parameters"></a>Параметры  
*RealType*  
По умолчанию тип с плавающей запятой имеет тип `double`. Возможные типы см. в разделе [\<random>](../standard-library/random.md).  
  
*РГСЧ*, механизм генератора случайных чисел. Возможные типы см. в разделе [\<random>](../standard-library/random.md).  
  
## <a name="remarks"></a>Примечания  
Класс шаблона описывает распределение "хи-квадрат", которое формирует значения указанного пользователем типа с плавающей запятой или типа `double`, если тип не указан. В следующей таблице представлены ссылки на статьи об отдельных членах.  
  
||||  
|-|-|-|  
|[chi_squared_distribution::chi_squared_distribution](../standard-library/chi-squared-distribution-class.md)|`chi_squared_distribution::n`|`chi_squared_distribution::param`|  
|`chi_squared_distribution::operator()`||[chi_squared_distribution::param_type](#chi_squared_distribution__param_type)|  
  
Функция свойства `n()` возвращает значение для хранимого параметра распределения `n`.  
  
Член свойства `param()` устанавливает или возвращает хранимый пакет параметров распределения `param_type`.  

Функции-члены `min()` и `max()` возвращают наименьший и наибольший из возможных результатов соответственно.  
  
Функция-член `reset()` удаляет любые кэшированные значения, чтобы результат следующего вызова `operator()` не зависел от любых значений, полученных от механизма перед вызовом.  
  
Функции-члены `operator()` возвращают следующее значение, созданное механизмом РГСЧ, из текущего или указанного пакета параметров.
  
Дополнительные сведения о классах распределения и их членах см. в разделе [\<random>](../standard-library/random.md).  
  
Подробные сведения о распределении "хи-квадрат" см. в статье Wolfram MathWorld [Распределение "хи-квадрат"](http://go.microsoft.com/fwlink/LinkId=400528).  
  
## <a name="example"></a>Пример  
  
```cpp  
// compile with: /EHsc /W4  
#include <random>   
#include <iostream>  
#include <iomanip>  
#include <string>  
#include <map>  
  
void test(const double n, const int s) {  
  
    // uncomment to use a non-deterministic generator  
    //    std::random_device gen;  
    std::mt19937 gen(1701);  
  
    std::chi_squared_distribution<> distr(n);  
  
    std::cout << std::endl;  
    std::cout << "min() == " << distr.min() << std::endl;  
    std::cout << "max() == " << distr.max() << std::endl;  
    std::cout << "n() == " << std::fixed << std::setw(11) << std::setprecision(10) << distr.n() << std::endl;  
  
    // generate the distribution as a histogram  
    std::map<double, int> histogram;  
    for (int i = 0; i < s; ++i) {  
        ++histogram[distr(gen)];  
    }  
  
    // print results  
    std::cout << "Distribution for " << s << " samples:" << std::endl;  
    int counter = 0;  
    for (const auto& elem : histogram) {  
        std::cout << std::fixed << std::setw(11) << ++counter << ": "  
            << std::setw(14) << std::setprecision(10) << elem.first << std::endl;  
    }  
    std::cout << std::endl;  
}  
  
int main()  
{  
    double n_dist = 0.5;  
    int samples = 10;  
  
    std::cout << "Use CTRL-Z to bypass data entry and run using default values." << std::endl;  
    std::cout << "Enter a floating point value for the \'n\' distribution parameter (must be greater than zero): ";  
    std::cin >> n_dist;  
    std::cout << "Enter an integer value for the sample count: ";  
    std::cin >> samples;  
  
    test(n_dist, samples);  
}  
```  
  
Первый запуск:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .5  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
n() == 0.5000000000  
Distribution for 10 samples:  
    1: 0.0007625595  
    2: 0.0016895062  
    3: 0.0058683478  
    4: 0.0189647765  
    5: 0.0556619371  
    6: 0.1448191353  
    7: 0.1448245325  
    8: 0.1903494379  
    9: 0.9267525768  
    10: 1.5429743723  
```  
  
Второй запуск:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): .3333  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
n() == 0.3333000000  
Distribution for 10 samples:  
    1: 0.0000148725  
    2: 0.0000490528  
    3: 0.0003175988  
    4: 0.0018454535  
    5: 0.0092808795  
    6: 0.0389540735  
    7: 0.0389562514  
    8: 0.0587028468  
    9: 0.6183666639  
    10: 1.3552086624  
```  
  
Третий запуск:  
  
```Output  
Use CTRL-Z to bypass data entry and run using default values.  
Enter a floating point value for the 'n' distribution parameter (must be greater than zero): 1000  
Enter an integer value for the sample count: 10  
 
min() == 4.94066e-324  
max() == 1.79769e+308  
n() == 1000.0000000000  
Distribution for 10 samples:  
    1: 958.5284624473  
    2: 958.7882787809  
    3: 963.0667684792  
    4: 987.9638091514  
    5: 1016.2433493745  
    6: 1021.9337111110  
    7: 1021.9723046240  
    8: 1035.7622110505  
    9: 1043.8725156645  
    10: 1054.7051509381  
```  
  
## <a name="requirements"></a>Требования  
**Заголовок:** \<random>  
  
**Пространство имен:** std  
  
##  <a name="a-namechisquareddistributionchisquareddistributiona--chisquareddistributionchisquareddistribution"></a><a name="chi_squared_distribution__chi_squared_distribution"></a>  chi_squared_distribution::chi_squared_distribution  
Формирует распределение.  
  
```  
explicit chi_squared_distribution(result_type n = 1.0);  
explicit chi_squared_distribution(const param_type& parm);
```  
  
### <a name="parameters"></a>Параметры  
*n*  
Параметр распределения `n`.  
  
*parm*  
 Структура параметров, используемая для формирования распределения.  
  
### <a name="remarks"></a>Примечания  
**Предусловие:** `0.0 < n`  
  
Первый конструктор создает объект, хранимое значение `n` которого содержит значение *n*.  
  
Второй конструктор создает объект, хранимые параметры которого инициализируются из *parm*. Вы можете получить и задать текущие параметры существующего распределения, вызвав функцию-член `param()`.  
  
##  <a name="a-namechisquareddistributionparamtypea--chisquareddistributionparamtype"></a><a name="chi_squared_distribution__param_type"></a>  chi_squared_distribution::param_type  
Сохраняет параметры распределения.  
  
```cpp    
struct param_type {  
   typedef chi_squared_distribution<result_type> distribution_type;  
   param_type(result_type n = 1.0);
   result_type n() const;
   
   bool operator==(const param_type& right) const;
   bool operator!=(const param_type& right) const;
   };  
```  

### <a name="parameters"></a>Параметры  
*n*  
Параметр распределения `n`.  
  
*right*  
Объект `param_type`, который требуется сравнить с данным объектом.  
  
### <a name="remarks"></a>Примечания  
**Предварительные условия:** `0.0 < n`  
  
Эту структуру можно передать конструктору класса распределения во время создания экземпляра, функции-члену `param()` для установки хранимых параметров существующего распределения и `operator()` для использования вместо хранимых параметров.  
  
## <a name="see-also"></a>См. также  
 [\<random>](../standard-library/random.md)




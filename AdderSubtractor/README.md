# <p align="center">Adder Subtractor System for Sign Bit Numbers</p>

<p align="center">
    <img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/interface.png" width="75%" height="75%" title="interface">
</p>

İşaret bitli 8-bit sayılar üzerinde toplama ve çıkarma işlemleri yapabilen sayısal sistem tasarımı. Bu tasarımda her bir durum (state) için bir flip-flop kullanılan “One Flip-Flop per State” metodu uygulanmıştır.

_**Not**: Aşağıda yer alan tüm sistemler işaret bitli 8-bit sayılar üzerinde toplama ve çıkarma yapan sayısal sistem için dizayn edilmiştir. Farklı, daha basit veya daha gelişmiş versiyonlar tasarlanabilir._

<br />

### Kısaltmalar

**As :** &nbsp;8-bit A sayısının işaret biti (Sign bit of A)  
**Bs :** &nbsp;8-bit B sayısının işaret biti (Sign bit of B)  
**Cin :** &nbsp;Elde girişi (Carry in)  
**Cout :** &nbsp;Elde çıkışı (Carry out)

<br /> 
<br />

# Alt Sistemler (Subsystems)

Sistem, belirli işlemler için özelleştirilmiş alt sistemlerden oluşmaktadır.

<br />

## 1-bit Tam Toplayıcı (Full-Adder)

1-bit iki sayıyı elde girişi  **_(Cin)_**  ile birlikte toplayarak toplam  **_(Sum)_**  ve elde  **_(Cout)_**  çıkışlarını veren sayısal sistem. 

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/full_adder_1_bit.png" width="60%" height="60%" title="1-bit full adder">

<br />
<br />

## 8-bit Tam Toplayıcı (Full-Adder)

1-bit Tam Toplayıcı'lar (Full-Adder) ile dizayn edilen, 8 bit iki sayıyı elde girişi  **_(Cin)_**  ile birlikte toplayarak toplam  **_(RESULT)_**  ve elde  **_(Cout)_**  çıkışlarını veren sayısal sistem.

![alt text](https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/full_adder_8_bit.png "8-bit full adder")

<br />
<br /> 

## Aritmetik İşlem Birimi (Arithmetic Circuit)

Seçim girişine **_(S1S0)_** verilen 2-bit değere göre 8-bit **_X_**, **_Y_** ve 1-bit **_Cin_** girişleri arasında farklı aritmetik işlemler gerçekleştirerek sonucu 8-bit **_R_** ve 1-bit **_Cout_** çıkışları ile veren sayısal sistem.

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/arithmetic_circuit.png" width="95%" height="95%" title="arithmetic circuit">

<br />
<br /> 

## Lojik İşlem Birimi (Logic Circuit)

Seçim girişine **_(S1S0)_** verilen 2-bit değere göre 8-bit **_A_** ve **_B_** sayıları arasında lojik işlemler gerçekleştirerek sonucu 8-bit **_R_** çıkışı ile veren sayısal sistem.

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/logic_circuit.png" width="60%" height="60%" title="logic circuit">

<br />
<br /> 

## Aritmetik Mantık Birimi (ALU - Arithmetic Logic Unit)

Aritmetik İşlem Birimi (Arithmetic Circuit) ve Lojik İşlem Birimi (Logic Circuit) sistemlerinin alt sistem olarak kullanıldığı sayısal sistem. Seçim girişine **_(S2S1S0)_** verilen 3-bit değere göre 8-bit **_A_**, **_B_** ve 1-bit **_Cin_** girişleri arasında farklı aritmetik veya lojik işlemler gerçekleştirerek sonucu 8-bit **_R_** ve 1-bit **_Cout_** çıkışları ile verir.

![alt text](https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/arithmetic_logic_unit.png "arithmetic logic unit")

<br />
<br /> 

## 1-bit Kaydedici (Register)

**_Load_** girişine 0 uygulandığında içerisindeki 1-bit sayıyı saklayan, 1 uygulandığında **_I (Input)_** girişine verilen 1-bit sayıyı **_Clk_** girişine uygulanan clock sinyalinin yükselen kenarında (rising edge) hafızasına alan sayısal sistem. İçerisinde sakladığı değer her an **_O (Output)_** çıkışında gözlenir. **_Reset_** girişine 1 verilerek içerisinde sakladığı değer sıfırlanabilir.

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/register_1_bit.png" width="50%" height="50%" title="1-bit register">

<br />
<br /> 

## 8-bit Kaydedici (Register)

8 adet 1-bit register kullanılarak dizayn edilen ve 1-bit register ile aynı mantıkta çalışarak 8-bit sayıyı saklayabilen sayısal sistem.

![alt text](https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/register_8_bit.png "8-bit register")

<br />
<br /> 

## İsteğe Bağlı Ters Alma (Optional Inverter)

İstenildiğinde girişine verilen 1-bit sayının tersini alan sayısal sistem. Seçim girişine **_(En)_** 0 verildiğinde girişi çıkışa aynen verirken, 1 verildiğinde girişin tersini alarak çıkışa verir.

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/optional_inverter.png" width="60%" height="60%" title="optional inverter">

<br />
<br /> 

## İşaret Biti Operatörü (Sign Bit Operator)
Seçim girişlerine bağlı olarak 1-bit iki giriş arasından birini seçen ve istenildiği taktirde tersini alan sayısal sistem. Girişlerle ilgili bir işlem yapıldığında **_Load_** çıkışına 1 verilir. Bu sayede işaret bitinde değişme olduğunda kendisinden sonra kullanılan register'ı uyararak yeni işaret bitini hafızaya almayı sağlar.

<br />

InputSelect = 0  &nbsp;  =>  &nbsp;  I _(Input)_ = A  
InputSelect = 1  &nbsp;  =>  &nbsp;  I _(Input)_ = B 

InvertSelect = 0  &nbsp;  =>  &nbsp;  O _(Output)_ = I  
InvertSelect = 1  &nbsp;  =>  &nbsp;  O _(Output)_ = I'

<br />

_InputSelect = S0, &nbsp; InvertSelect = S1 için;_

<table>
<tr><th>Selections</th><th>Load Signal</th></tr>
<tr><td>

|S1   |S0   |I    |O    |
|:---:|:---:|:---:|:---:|
|0    |0    |A    |A    |
|0    |1    |B    |B    |
|1    |0    |A    |A'   |
|1    |1    |B    |B'   |

</td><td>

|Load |S1   |S0   |
|:---:|:---:|:---:|
|0    |0    |0    |
|1    |0    |1    |
|1    |1    |0    |
|1    |1    |1    |

</td></tr> </table>

<br />

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/sign_bit_operator.png" width="50%" height="50%" title="sign bit operator">

<br /> 
<br />
<br /> 

# Tasarım (Design)

İşaret bitli sayılar arasında toplama ve çıkarma işlemlerini gerçekleştirebilen sistemin tasarımı.

<br />

## Sistem Akış Diyagramı (Flow-Chart Diagram)

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Diagrams/FlowChart_Diagram/AdderSubtractor_FlowChartDiagram.png"  width="60%" height="60%" title="Flow-Chart Diagram">

<br />
<br />  

## Durum Makine Diyagramı (State Machine Diagram)

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Diagrams/State_Machine_Diagram/AdderSubtractor_StateMachineDiagram.png" width="50%" height="50%" title="State Machine Diagram">

<br />
<br />  

## Durumlar ve Yapılan İşlemler (States and Operations)

Akış diyagramında tasarlanan işleyişi gerçeklemek üzere işlemler, durum makine diyagramındaki durumlara **_(T)_** bölünürse:

| &nbsp; States &nbsp; | &nbsp; &nbsp; &nbsp; Operations &nbsp; &nbsp; &nbsp; |
|:------:|--------------------------------------------------|
|**T0**  | &nbsp; X = 1 <br />  &nbsp; _(Initialization)_   |
|**T1**  | &nbsp; Bs <- Bs' <br /> &nbsp;                   |
|**T2**  | &nbsp; As : Bs <br />  &nbsp; _(No operation)_   |
|**T3**  | &nbsp; A <- A + B <br />  &nbsp; E <- Cout       |
|**T4**  | &nbsp; A <- A + B' + 1 <br />  &nbsp; E <- Cout  |
|**T5**  | &nbsp; check E <br />  &nbsp; _(No operation)_   |
|**T6**  | &nbsp; A <- A' <br /> &nbsp;                     |
|**T7**  | &nbsp; A <- A + 1 <br />  &nbsp; As <- As'       |  

_**Not:** Her bir state'deki (T) işlemler bir clock pulse süresi içerisinde gerçekleştirilir._

<br />
<br /> 

## Kontrol Girişleri (Control Inputs)

**qa** = Toplama işlemi _(toplama işlemi seçilirse qa = 1)_  
**qs** = Çıkarma işlemi _(çıkarma işlemi seçilirse qs = 1)_  
&nbsp;**S**  &nbsp;= As ile Bs eşitliği _(A ve B sayılarının işaretleri farklıysa S = 1)_  
&nbsp;**E**  &nbsp;= İşlem eldesi _(işlem sonucunun eldesi varsa E = 1)_

<br />
<br /> 

## Kontrol Çıkışları (Control Signals)

**X &nbsp; &nbsp; :** &nbsp;E'yi temizle (clear E) (initial state)  
**Y &nbsp; &nbsp; :** &nbsp;Bs'nin değilini al (complement Bs)  
**Z &nbsp; &nbsp; :** &nbsp;As'nin değilini al (complement As)  
**S2 S1 S0 :** &nbsp;Uygun işlemi seç (select operation)  
**Cin &nbsp;:** &nbsp;ALU işlemine yardımcı (assist ALU operation)  
**L &nbsp; &nbsp; :** &nbsp;Yükle (Load)

<p align="center">
    <img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Diagrams/Control_Unit_Block_Diagram/AdderSubtractor_ControlUnitBlockDiagram.png" width="35%" height="35%" title="Control Unit Block Diagram">  
</p>  
<p align="center">Control Unit Block Diagram</p>

<br />

Durumlarda (states) gerçekleştirilen işlemler sonrasında kontrol sinyallerinin değerleri:
|                                                                             |X   |S2  |S1  |S0  |Cin |L   |Y   |Z   |
|-----------------------------------------------------------------------------|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|**T0:** &nbsp;_X = 1 <br /> &nbsp; &nbsp; &nbsp; &nbsp;(Initialization)_     |1   |0   |0   |0   |0   |0   |0   |0   |
|**T1:** &nbsp;_Bs <- Bs' <br/> &nbsp;_                                       |0   |0   |0   |0   |0   |0   |1   |0   |
|**T2:** &nbsp;_As : Bs <br /> &nbsp; &nbsp; &nbsp; &nbsp;(No operation)_     |0   |0   |0   |0   |0   |0   |0   |0   |
|**T3:** &nbsp;_A <- A + B <br /> &nbsp;_                                     |0   |0   |0   |1   |0   |1   |0   |0   |
|**T4:** &nbsp;_A <- A + B' + 1 <br /> &nbsp; &nbsp; &nbsp; &nbsp;E <- Cout_  |0   |0   |1   |0   |1   |1   |0   |0   |
|**T5:** &nbsp;_check E <br /> &nbsp; &nbsp; &nbsp; &nbsp;(No operation)_     |0   |0   |0   |0   |0   |0   |0   |0   |
|**T6:** &nbsp;_A <- A' <br /> &nbsp;_                                        |0   |1   |1   |1   |0   |1   |0   |0   |
|**T7:** &nbsp;_A <- A + 1 <br /> &nbsp; &nbsp; &nbsp; &nbsp;As <- As'_       |0   |0   |0   |0   |1   |1   |0   |1   |

<br />
<br /> 

## Kontrol Birimi (Control Unit)

_One flip-flop per state_ metoduna göre her state için kullanılan D flip-flop'ların **_(FF)_** her birinin girişi _**(D)**_ için denklemler:

**D0** = qa'qs' T0 + T3 + T5 E + T7  
**D1** = qs T0  
**D2** = qa T0 + T1  
**D3** = T2 S'  
**D4** = T2 S  
**D5** = T4  
**D6** = T5 E'  
**D7** = T6
  
<br />

Sistemi, tasarım doğrultusunda kontrol etmek üzere kontrol sinyallerinin durumlar (states) türünden denklemleri:

**X &nbsp; &nbsp;:** &nbsp;T0  
**S2 &nbsp;:** &nbsp;T6  
**S1 &nbsp; :** &nbsp;T4 + T6  
**S0 &nbsp;:** &nbsp;T3 + T6  
**Cin :** &nbsp;T4 + T7  
**L &nbsp; &nbsp;:** &nbsp;T3 + T4 + T6 + T7  
**Y &nbsp; &nbsp;:** &nbsp;T1  
**Z &nbsp; &nbsp;:** &nbsp;T7

<br /> 

Kontrol birimi (control unit) gerçeklemesi:

![alt text](https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/control_unit.png "control unit")

<br />
<br /> 

## Toplayıcı-Çıkarıcı Sistem (Adder-Subtractor)

Toplayıcı-Çıkarıcı sistem tasarımı:

<img src="https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Diagrams/System_Design_Diagram/AdderSubtractor_SystemDesignDiagram.png" width="45%" height="45%" title="System Design Diagram">

<br />

Toplayıcı-Çıkarıcı sistem gerçeklemesi:  

![alt text](https://github.com/abdullahdangac/Digital-System-Design/blob/main/AdderSubtractor/Images/Components/adder_subtractor_system.png "adder subtractor system")
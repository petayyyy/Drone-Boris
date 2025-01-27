<font size=6> **Создание автономного воздушного робота с нуля** </font>

Это сопутствующий документ к видеоуроку [Создание автономного воздушного робота с нуля] (https://www.bilibili.com/video/BV1WZ4y167me?p=1), ссылка на github - https://github.com/ZJU-FAST-Lab/Fast-Drone-250

<font color="#dd0000">Вопросы безопасности</font>

Беспилотные летательные аппараты Quadcopter несут в себе высокий риск безопасности. Просим студентов строго соблюдать правила безопасности, не проводить испытания в помещении или на открытом воздухе в присутствии людей, а также нести ответственность за собственную безопасность и безопасность окружающих, от которой данная лаборатория полностью освобождает.


- [Глава 1: Введение в курс](#глава-1-введение-в-курс)
- [Глава 2: Сварка с установленной мощностью](#глава-2-сварка-в-силовой-рубашке)
- [Глава 3: Установка и подключение органов управления полетом](#глава-3-установка-и-подключение-органов-управления-полетом)
- [Глава 4: Настройка системы управления полетом и испытательные полеты](#глава-4-настройка-управления-полетом-и-испытательные-полеты)
- [Глава 5: Установка бортового компьютера и датчиков](#глава-5-установка-бортового-компьютера-и-датчиков)
- [Глава 6: Установка Ubuntu 20.04](#Глава 6: Установка ubuntu 2004)
- [Глава 7: Экологическая конфигурация бортового компьютера](#Глава 7 Экологическая конфигурация бортового компьютера)
- [Глава 8: Установка и использование часто используемого программного обеспечения для проведения экспериментов и ввода в эксплуатацию](# Глава 8 Установка и использование общего программного обеспечения для экспериментов и отладки)
- [Глава 9: Введение в рамки и параметры кода Эго-Планнера](#Глава 9: Введение в рамки и параметры кода эго-планировщика)
- [Глава 10: Настройка параметров и внешняя калибровка VINS](#Глава 10 Настройка параметров и внешняя эталонная калибровка винтов)
- [Глава 11: Эксперименты с Эго-планировщиком](#Глава 11: Эксперименты с эго-планировщиком)
- [Q & A Часто задаваемые вопросы и ответы](#qa- Часто задаваемые вопросы и ответы)

## Глава 1: Введение в курс
  Этот курс - бесплатный курс для студентов, энтузиастов и практиков, интересующихся автономными воздушными роботами, и включает полный набор подробных процедур от сборки оборудования, настройки бортовой компьютерной среды, развертывания кода, экспериментов в реальных условиях и т.д. Он проведет вас с нуля до сборки собственного автономного дрона и позволит ему свободно перемещаться по неизвестным средам. Весь код и аппаратные конструкции, задействованные в этом курсе, имеют открытый исходный код, <font color="#dd0000">Коммерциализация и воспроизведение строго запрещены. Авторские права и окончательная интерпретация принадлежат лаборатории FASTLAB, Чжэцзянский университет.
  Основное внимание в этом курсе уделяется созданию, развертыванию и отладке кода автономных воздушных роботов, а также некоторым теоретическим основам автономных воздушных роботов, таким как модели динамики, поиск пути, планирование траектории, построение карты и т.д. Г-н Гао Фей имеет очень подробный и углубленный [курс](https://www.shenlanxueyuan.com/) в Deep Blue College. course/385?source=1), поэтому я не буду повторять его в этом курсе.
  
## Глава 2: Сварка с установленной мощностью
  Дополнительную информацию о корпусе робота и сварочных инструментах см. в [purchase_list.xlsx](purchase_list.xlsx), а вопросы о выборе оборудования см. в разделе Дополнительно 1: Выбор оборудования.
## Глава 3: Установка и подключение органов управления полетом
* Обязательно обратите внимание на последовательность сигнальных проводов ESC!!!
  <img src="images\电机方向.jpg" alt="电机方向" style="zoom: 15%;" />
* Стрелки управления полетом ориентированы в том же направлении, что и нос для положительной ориентации, также возможно любое направление, повернутое на угол, кратный 90°, и может быть впоследствии отрегулировано в настройках управления полетом, рекомендуется такое же расположение ориентации, как на видео.
* <font color="#dd0000">Настоятельно рекомендуется использовать силиконовый дуплексный кабель, поскольку обычный дуплексный кабель слишком жесткий и склонен к плохому контакту.</font>
* Изолируйте модуль 5 В черной изолентой и наклейте вокруг него толстый круг губчатой ленты, чтобы предотвратить повреждение модуля 5 В при посадке самолета, или рассмотрите возможность привязывания модуля 5 В к боковой стороне руки с помощью кабельной стяжки.
* Используйте систему управления полетом V5+ или другую систему управления полетом, которая разделяет аналоговые и цифровые выходы (с выходами, обозначенными A1~A4 M1~M4), и если вы хотите использовать протокол Dshot, подключите порт A

## Глава 4: Настройка системы управления полетом и испытательные полеты

* Пожалуйста, запишите прошивку `/firmware/px4_fmu-v5_default.px4` в этом git-проекте, эта прошивка скомпилирована из официальной прошивки версии 1.11.0, вы можете скомпилировать ее самостоятельно, если вам это необходимо. Версия 1.13 была проверена на наличие ошибок и не рекомендуется. Более ранние версии прошивки не тестировались.

* Создайте `/etc/extras.txt` в корневом каталоге sd-карты системы управления полетом и напишите

  ```
  mavlink stream -d /dev/ttyACM0 -s ATTITUDE_QUATERNION -r 200
  mavlink stream -d /dev/ttyACM0 -s HIGHRES_IMU -r 200
  ```
  
  Увеличить частоту выпусков imu	
  
* Измените тип стойки на `Generic 250 Racer` для обозначения модели с колесной базой 250 мм. Для других размеров рам, пожалуйста, выберите тип рамы в соответствии с фактической колесной базой

* Измените `dshot_config` на dshot600

* Измените `CBRK_SUPPLY_CHK` на 894281 * Выполнение этого шага пропускает проверку питания, поэтому не имеет значения, если раздел настроек батареи в левой колонке красный*.

* Измените `CBRK_USB_CHK` на 197848

* Измените `CBRK_IO_SAFETY` на 22027

* Измените `SER_TEL1_BAUD` на 921600

* Измените `SYS_USE_IO` на 0 (игнорировать, если поиск не ведется)

* Перед включением питания, пожалуйста, используйте мультиметр, чтобы проверить, не закорочены ли положительные и отрицательные паяные соединения. Настоятельно рекомендуется подключить [устройство защиты от короткого замыкания] (https://item.taobao.com/item.htm?spm=a230r.1.14.6.72b83b20uNbZk7&id=656973651729&ns) перед первым включением питания. =1&abbucket=19#detail)

* <font color="#dd0000">Убедитесь, что пропеллер не установлен, прежде чем проверять рулевое управление двигателя ！！！！.</font>

* Изменение управления двигателем: перейдите в консоль mavlink

  ```
  dshot reverse -m 1
  dshot save -m 1
  ```

  Измените `1` на серийный номер реверсируемого двигателя
  
* <font color="#dd0000">Пожалуйста, убедитесь, что вам помогает пилот, который имеет опыт первого полета в режиме самостабилизации. 99% пилотов, которые летали только на дронах DJI, не смогут управлять ими должным образом!</font>

* Что делать, если рядом нет опытного летуна? См. вопросы и ответы для получения подробной информации


## Глава 5: Установка бортового компьютера и датчиков

* Карбоновая пластина была зарезервирована для установки NUC в разобранном корпусе. Если вы хотите разобрать корпус для установки NUC, вам необходимо приобрести дополнительную сетевую карту USB или снять антенну сетевой карты, которая идет в комплекте, чтобы найти место для ее крепления, а поскольку плата из углеродного волокна является проводящей, пожалуйста, убедитесь, что вы поддерживаете NUC с помощью нейлоновой стойки, пожалуйста, проверьте соответствующую информацию самостоятельно.
* Бортовой компьютер питается непосредственно от аккумулятора модели 4S, что вполне нормально в обычных условиях. Однако теоретически желательно подключить регулятор напряжения, иначе бортовой компьютер отключится, когда дрон взорвется/аккумулятор будет почти разряжен. Однако, поскольку модули регуляторов напряжения, соответствующие мощности NUC, относительно велики, пожалуйста, используйте усмотрение вашего студента.

## Глава 6: Установка Ubuntu 20.04

* Адрес зеркального сайта: `http://mirrors.aliyun.com/ubuntu-releases/20.04/` Скачать `ubuntu-20.04.4-desktop-amd64.iso`.
* Официальный сайт программы для записи UltraISO: `https://cn.ultraiso.net/`.
* Настройки разделов：
  * Системный раздел EFI (основной раздел) 512M
  * Пространство подкачки (логический раздел) 16000M (в два раза больше объема памяти)
  * Точка монтирования `/` (основной раздел) весь оставшийся объем
  * <font color="#dd0000">Вам также потребуется установить ubuntu на ваш ноутбук, рекомендуется версия 20.04. Подойдет как виртуальная машина, так и двойная система, но двойная система рекомендуется, если у вас есть долгосрочные планы обучения</font>
## Глава 7: Конфигурация среды бортового компьютера 

* установка РОС 
  * `sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'`
  * `sudo apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key C1CF6E31E6BADE8868B172B4F42ED6FBAB17C654`
  * `sudo apt update`
  * `sudo apt install ros-noetic-desktop-full`
  * `echo "source /opt/ros/noetic/setup.bash" >> ~/.bashrc`
  * Учащимся, не знакомым с ROS, рекомендуется сначала изучить вводное руководство по ROS от Гуюджу на языке Bilibili. 
* тест ROS
  * Откройте терминал и войдите 
  * `roscore`
  * `rosrun turtlesim turtlesim_node`
  * `rosrun turtlesim turtle_teleop_key`
* установка драйвера реалсенс 
  * `sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key  F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE || sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-key  F6E65AC044F831AC80A06380C8B3A55A6F3EFCDE`
  * `sudo add-apt-repository "deb https://librealsense.intel.com/Debian/apt-repo $(lsb_release -cs) main" -u`
  * `sudo apt-get install librealsense2-dkms`
  * `sudo apt-get install librealsense2-utils`
  * `sudo apt-get install librealsense2-dev`
  * `sudo apt-get install librealsense2-dbg`
  * тест: `realsense-viewer`
  * Обратите внимание, что подключенный порт USB должен быть 3.x (синий).
* Установка mavros
  * `sudo apt-get install ros-noetic-mavros`
  * `cd /opt/ros/noetic/lib/mavros`
  * `sudo ./install_geographiclib_datasets.sh`
* установка ceres, glog и ddyanmic-reconfigure 
  * распаковать `3rd_party.zip`
  * Откройте терминал и введите ./glog 
  * `./autogen.sh && ./configure && make && sudo make install`
  * `sudo apt-get install liblapack-dev libsuitesparse-dev libcxsparse3.1.2 libgflags-dev libgoogle-glog-dev libgtest-dev`
  * Откройте терминал и введите ./ceres 
  * `mkdir build`
  * `cd build`
  * `cmake ..`
  * `sudo make -j4`
  * `sudo make install`
  * `sudo apt-get install ros-noetic-ddynamic-reconfigure`
* Скачайте код эго-планировщика и скомпилируйте 
  * `git clone https://github.com/ZJU-FAST-Lab/Fast-Drone-250`
  * `cd Fast-Drone-250`
  * `catkin_make`
  * `source devel/setup.bash`
  * `roslaunch ego_planner single_run_in_sim.launch`
  * Нажмите клавишу G на клавиатуре в Rviz, затем щелкните левой кнопкой мыши, чтобы выбрать целевую точку дрона. 

## Глава 8: Установка и использование часто используемого программного обеспечения для проведения экспериментов и ввода в эксплуатацию

* VScode：`sudo dpkg -i ***.deb`
* Terminator：`sudo apt install terminator`
* Plotjuggler：
  * `sudo apt install ros-noetic-plotjuggler`
  * `sudo apt install ros-noetic-plotjuggler-ros`
  * `rosrun plotjuggler plotjuggler`
* Net-tools：
  * `sudo apt install net-tools`
  * `ifconfig`
* ssh：
  * `sudo apt install openssh-server`
  * В блокноте：`ping 192.168.**.**`
  * `sudo gedit /etc/hosts`
  * Добавить строку：`192.168.**.** fast-drone`
  * `ping fast-drone`
  * `ssh fast-drone@fast-drone`(`ssh Имя пользователя@Альтернативное имя`)

## Глава 9: Введение в рамки и параметры кода Эго-Планнера
* В разделе `src/planner/plan_manage/launch/single_run_in_exp.launch`.
  * `map_size`: необходимо изменить, если размер вашей карты велик, будьте осторожны, чтобы не превысить map_size/2 для целевых точек
  * `fx/fy/cx/cy`: модификация фактической внутренней ссылки вашей камеры глубины (как ее увидеть, мы рассмотрим в следующем уроке).
  * `max_vel/max_acc`: модификация для настройки максимальной скорости, ускорения. Рекомендуется начинать с 0,5 для пробного полета, не превышать 2,5 максимум и не превышать 6 ускорение
  * `flight_type`: 1 для режима выбора точек rviz, 2 для режима отслеживания путевых точек
* `src/planner/plan_manage/launch/advanced_param_exp.xml` под.
  * ``разрешение``: представляет разрешение точек сетки растровой карты, в метрах. Чем он меньше, тем мельче карта, но тем больше памяти она занимает. Минимальное значение не должно быть меньше 0,1
  * `obstacles_inflation`: представляет размер раздувания препятствий в метрах. Рекомендуется установить значение, по крайней мере, в 1,5 раза больше радиуса самолета (включая пропеллер и лопасти), но не более чем в 4 раза больше `разрешения`. Если самолет имеет большую колесную базу, пожалуйста, увеличьте `разрешение` соответствующим образом
* В разделе `src/realflight_modules/px4ctrl/config/ctrl_param_fpv.yaml`.
  * `mass`: изменение фактического веса дрона
  * `hover_percent`: модифицирован дроссель зависания дрона, который можно посмотреть через px4log, см. [документацию](https://www.bookstack.cn/read/px4-user-guide/zh-log-flight_review.md) Если ваш дрон является точно такой же, как и курс, этот показатель останется равным 0,3. Отрегулируйте этот параметр, если изменилась силовая установка, или изменился вес, или изменилась колесная база, иначе автоматический взлет будет происходить без взлета или с сильным перебором.
  * `gain/Kp,Kv`: Это член ПИ в ПИД, который обычно не нужно сильно изменять. Если происходит завышение, пожалуйста, отрегулируйте его соответствующим образом. Если реакция дрона медленная, пожалуйста, отрегулируйте ее соответствующим образом.
  * `rc_reverse`: Этот пункт не является необходимым для тех, кто использует LODI AT9S. Если вы обнаружили, что самолет летит в направлении, противоположном качалке во время автоматического взлета в уроке 11, это означает, что вам необходимо модифицировать этот пункт, изменив значение, соответствующее противоположному каналу, на true. в реальных экспериментах дроссель более опасен, если он обратный, рекомендуется подтвердить это перед взлетом, шаги следующие
    * `roslaunch mavros px4.launch`.
    * `rostopic echo /mavros/rc/in`
    * Включите пульт дистанционного управления и поверните дроссельную заслонку пульта дистанционного управления от минимального полного до максимального значения
    * Посмотрите на эхо-сообщение, чтобы увидеть, какой элемент медленно изменяется (это значение канала дросселирования), и посмотрите, изменяется ли оно от малого к большому.
    * Если он изменяется от малого к большому, вам не нужно изменять rc_reverse дросселя, вместо этого измените его на true.
    * То же самое для других каналов
  
## Глава 10: Настройка параметров и внешняя калибровка VINS
* Проверьте правильность подключения mavros устройств управления полетом
  * `ls/dev/tty*', подтвердите, что последовательный порт системы управления полетом подключен нормально.Обычно `/dev/ttyACM0`
  * 'sudo chmod 777/dev/ttyACM0`, дополнительные разрешения для последовательного порта
  * `roslaunch mavros px4.launch`
  * `rostopic hz /mavros/imu/data_raw`，Подтвердите, что частота imu передачи управления полетом составляет около 200 Гц
* Убедитесь, что драйвер realsense работает нормально
  * `roslaunch realsense2_camera rs_camera.launch`
  * Войдите на удаленный рабочий стол，`rqt_image_view`
  * проверить`/camera/infra1/image_rect_raw`,`/camera/infra2/image_rect_raw`,`/camera/depth/image_rect_raw`Темы нормальные
* VINS Настройка параметров
  * Доступ`realflight_modules/VINS_Fusion/config/`
  
  * Привод realsense После，`rostopic echo /camera/infra1/camera_info`，Положите матрицу K, в которой fx,fy,cx,cy Заполнить`left.yaml`и`right.yaml`
  
  * Создайте папку `vins_output` в домашнем каталоге (если ваше имя пользователя не является fast-drone, вам нужно изменить vins_out_path в конфигурации, чтобы он был абсолютным путем к папке, которую вы фактически создали)
  
  * Модифицируйте `fast-drone-250.yaml`.Четвертый столбец матрицы "данные" yaml "body_t_cam0" и "body_T_cam1" - это фактические внешние параметры камеры вашего дрона относительно системы управления полетом. Единица измерения - метры, а порядок - x /y /Z. Четвертый элемент равен 1, изменять его не нужно.
  
* VINS Точная самокалибровка внешних параметров
  * `sh shfiles/rspx4.sh`
  * `rostopic echo /vins_fusion/imu_propagate`
  * Возьмите самолет и пройдитесь по площадке как можно медленнее, освещение в зале не должно сильно меняться, освещение не должно быть слишком темным, не используйте стробоскопические источники света, старайтесь поставить как можно больше всякой всячины увеличьте характерные точки, которые VINS использует для сопоставления. 
  * Пучок vins_output/extrinsic_parameter.txt заменить содержимое fast-drone-250.yaml из body_T_cam0а также body_T_cam1
  * Повторяйте вышеуказанную операцию до тех пор, пока отклонение данных одометра VINS не сойдется к удовлетворительному значению после нескольких кругов (обычно в пределах 0,3 метра). 
* Проверка модуля сопоставления 
  * `sh shfiles/rspx4.sh`
  * `roslaunch ego_planner single_run_in_exp.launch`
  * войти в удаленный рабочий стол `roslaunch ego_planner rviz.launch`

## Глава 11: Эксперименты с Эго-планировщиком
* Автоматический взлет：

  * sh shfiles/rspx4.sh
  * rostopic echo /vins_fusion/imu_propagate
  * Поднимите робота и медленно снимите его в небольшом диапазоне. Поставив его на место, убедитесь, что VINS в небольшом отклонении.
  * Канал 5 RC набран на внутреннюю сторону. Канал 6 набран на нижнюю сторону. Дроссель установлен по центру.
  * roslaunch px4ctrl run_ctrl.launch
  * sh shfiles/takeoff.sh, Если пропеллер самолета начинает вращаться, но не может взлететь, значит hover_percent слишком мал. Если летательный аппарат пролетает более 1 метра перед снижением, параметр hover_percent слишком велик.
  * Вы можете управлять положением дрона так же, как управляете DJI
  * При посадке установите дроссельную заслонку на самый низкий уровень. После того, как дрон окажется на земле, установите канал 5 на середину, а левый стик переместите в левый нижний угол, чтобы зафиксировать его.

* Эксперимент
  * Автоматический взлет
  * roslaunch ego-planner single_run_in_exp.launch
  * sh shfiles/record.sh
  * Войдите в удаленный рабочий стол, roslaunch ego_planner rviz.launch
  * Нажмите клавишу G и левой кнопкой мыши щелкните по целевой точке, чтобы заставить дрон лететь.

* Что делать, если во время эксперимента произойдет несчастный случай! ! !
    * случай 1: Нет проблем с позиционированием VINS, но несвоевременное планирование/неточное отображение заставляет дрон планировать траекторию, которая может врезаться в препятствие. Если пилот обнаружит, что дрон может врезаться в препятствие во время полета, поверните канал 6 обратно в верхнюю сторону перед столкновением. Дрон выйдет из режима следования по траектории и перейдет в режим зависания VINS. Затем безопасно посадите беспилотник.
     * случай 2: Неточное позиционирование VINS, проявляется в виде сильного дрожания самолета/очевидного несоблюдения нормальной траектории или быстрого подъема или быстрого спуска и т.д. В это время бесполезно набирать канал 6. Вы должны повернуть канал 5 обратно в среднее положение. Заставьте робота полностью выйти из программного управления и вернуться в стабилизированный режим RC. Затем приземлитесь
     * случай 3: Дрон столкнулся с препятствием и еще не упал на землю. В это время наберите канал 6, чтобы проверить, может ли самолет стабилизироваться. Если нет, наберите канал 5, чтобы приземлиться вручную
     * случай 4: Дрон врезался в препятствие и упал на землю. Наберите канал 5, чтобы немедленно заблокировать его, чтобы уменьшить материальный ущерб
     * случай 5: последнее средство Если вы не можете понять, что это за случай, или самолет летит в сторону очень опасной зоны, наберите канал 7, чтобы напрямую остановить пропеллеры. Таким образом, самолет напрямую потеряет мощность и упадет, что приведет к большим повреждениям фюзеляжа самолета. В общем, это не рекомендуется в условиях низкой скорости.


## Q & A Часто задаваемые вопросы и ответы

В: Могу ли я использовать 265+435, чтобы не запускать вайны?
О: Да, но скорость 265 прямо с одометра оценивается как проблематичная и может привести к неустойчивому управлению. Нужно сделать ekf fusion из 265 и imu.

В: Могу ли я заменить xxx в списке оборудования?
О: Пожалуйста, посмотрите дополнительное видео, в котором объясняется большинство возможностей замены.
   Параметры pid необходимо настроить соответствующим образом.
   Камеру 435 можно заменить камерой 430. 430 дешевле, но не имеет корпуса, плохо фиксируется и может легко взорваться.
   Замена батареи не рекомендуется, поскольку рама Q250 на трассе достаточно велика для установки батареи 2300mah 4S и не требует дополнительного крепления. При замене батареи вам придется самостоятельно разобраться с ее размещением.

В: Могу ли я запускать вины с imu, который поставляется с D435i?
О: Нет, потому что иму 435 очень шумный.

В: Есть ли какие-либо изменения в прошивке v1.11.0, поставляемой вместе с курсом? Обязательно ли использовать эту прошивку?
О: Изменений нет, это прямая загрузка с официального сайта px4. Этот код был протестирован только на этой версии, на версии v1.13 он не сработал, так как VINS часто падает. Другие системы управления полетом/другие версии прошивки не тестировались, поэтому при необходимости вы можете протестировать их самостоятельно.

В: Что делать, если двигатель не вращается при проверке QGC?
A: 1. Проверьте, поддерживает ли ESC функцию dshot, если нет, пожалуйста, проверьте метод калибровки pwm ESC самостоятельно. 
   2. Если вы используете систему управления полетом V5+ или другую систему управления полетом с отдельным аналоговым и цифровым выходом (характеризуется выходным портом, обозначенным A1~A4 M1~M4), если вы хотите использовать протокол Dshot, пожалуйста, подключите порт A.
   3. если вы используете holybro pixhawk4 полной версии, пожалуйста, подключите FMU PWM OUTPUT вместо I/O PWM OUTPUT.

Вопрос: Возникает ли красная ошибка после запуска vins?
О: Возможно, вы изменили конфигурацию и формат неправильный, пожалуйста, измените соответствующую конфигурацию в соответствии с ошибкой.

Вопрос: Что означает ошибка "VINS_RESULT_PATH не открыт" после запуска vins?
A: Создайте папку `vins_output` в вашем домашнем каталоге (если ваше имя пользователя не fast-drone, вам нужно изменить vins_out_path в конфигурации на абсолютный путь к папке, которую вы действительно создали)

В: Какова грузоподъемность этого самолета? Каков диапазон? Как далеко он может улететь?
О: Взлетный вес без дополнительной нагрузки составляет около 1,1-1,2 кг, максимальный взлетный вес находится в пределах 1,8 кг, больше - нестабильно, а дальность полета очень мала.
	Дальность стрельбы без нагрузки составляет около 5 минут.
	Дальность полета зависит от качества связи wifi, обычно wifi может поддерживать связь на расстоянии до 100 м. Кроме того, поскольку растровая карта открывается непосредственно в памяти, если диапазон карты установлен слишком большим, она легко заполнит память и приведет к медленной работе других программ. Обычно не рекомендуется превышать размер 50м*50м.
	
В: Почему мне нужно блокировать структурированный свет фотокамеры D435?
О: Смысл структурированного света в том, чтобы сделать карту глубины, полученную камерой, более точной, но на бинокулярном изображении будет видно пятно света с фиксированным положением, что не очень хорошо для работы VIO, поэтому его нужно отключить.

В: А как насчет дрифта ВИНС?
О: 1. Проверьте наличие сильно отражающих объектов в окружающей среде (плитка, стекло и т.д.).
   2. перемещайте дрон как можно медленнее, чтобы в кадре не было движущихся объектов
   3. постарайтесь как можно точнее измерить исходные внешние параметры
   4. не запускайте rviz на удаленном рабочем столе во время работы vins (это займет много ресурсов процессора), если вы действительно хотите это сделать, мы рекомендуем использовать ROS Multi, а затем открыть его на вашем ноутбуке
   5. проверьте, есть ли в окружающей среде источник стробоскопического света (не виден невооруженным глазом, проверьте в монокулярный экран реалсенса)

В: У меня нет опыта управления самостабилизирующимся дроном, и рядом со мной нет опытных пилотов, что мне делать?
A: 1. Если у вас есть бюджет, мы рекомендуем вам купить прочный дрон с защитным кольцом для практики, рекомендуемые модели: mobula6, Geelong Goldfish 85x, Dragonracewhoop30 и т.д.
   Если у вас нет бюджета, мы рекомендуем приобрести донгл для подключения пульта AT9S, рекомендованного в курсе, к компьютеру, а затем потренироваться в симуляторе. Рекомендуемый симулятор - liftoff на steam, free rider рекомендуется бесплатно.

В: Я хочу использовать NX в качестве бортового компьютера, что еще нужно сделать?
О: В принципе, новичкам не рекомендуется использовать NX, это будет много работы, и данный курс не охватывает ее, а у ассистентов преподавателя нет времени, чтобы помочь вам с этим.
   Необходимо выполнить следующие дополнительные действия.
   1. изменить VINS на GPU версию, так как CPU арифметика NX очень плохая и CPU версия VINS с запущенным курсом не будет работать
   2. устранить проблемы с креплением и питанием NX
   3. устранить проблему с фиксацией реальности
   4. решить проблему недостаточного количества интерфейсов при использовании небольшой базовой платы для NX
   5. решить ряд проблем, вызванных несовместимостью между arm и x86
   
Вопрос: Я следовал руководству по изменению файла etc/extra.txt в sdcard, но частота IMU не изменилась на 200 Гц.
A: Возможная причина в том, что ваша прошивка не поддерживает это изменение, попробуйте выполнить следующее после запуска mavros
rosrun mavros mavcmd long 511 105 5000 0 0 0 0 0 0 0 0 & sleep 1;
rosrun mavros mavcmd long 511 31 5000 0 0 0 0 0 0 0 0 & sleep 1;

Переведено с помощью www.DeepL.com/Translator (бесплатная версия)
	   
	Q: 我按照教程修改sd卡里的etc/extra.txt后，IMU频率没有变成200hz怎么办？
	A: 可能原因是你的固件不支持这样修改，可以尝试在启动mavros后执行：
	rosrun mavros mavcmd long 511 105 5000 0 0 0 0 0 & sleep 1;
	rosrun mavros mavcmd long 511 31 5000 0 0 0 0 0 & sleep 1;
	


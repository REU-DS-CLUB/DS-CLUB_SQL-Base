# DATA SCINCE CLUB SQL Database

Целью этого проекта является создание базы данных. Которрая будем отображать в себе:
* Информацию о членах клуба
* Сведение о мероприятиях
* Проекты которые ведет клуб
* Департаменты 

| Название файла/директории | Содержание файла |
|----:|:----------|
| conceptual model | папка с концептуальной моделью базы данных|
| Docker-DBeamer_run_instruction.pdf | pdf файл с инструкцией как запустить базу данных через Docker и DBeamer|
| database_description.docx | docx файл с описанием предметной области базы данных|
| datalogical_relational_database_model.mwb | mwb файл с даталогической реляционной модели базы данных|

## ОПИСАНИЕ ПРЕДМЕТНОЙ ОБЛАСТИ 
REU Data Science Club - сообщество, созданное командой студентов РЭУ им. Плеханова, активно развивающихся в Data Science и готовых помогать всем желающим получать необходимые знания и навыки в этой области :)
### Структура клуба
•	Руководитель клуба и его заместитель
Роль руководителя заключается в поддержке всей деятельности клуба, в осуществлении стратегического планирования и в поддержании работы департаментов.
•	Департаменты
Сейчас в клубе действуют 5 департаментов: 
1.	Event – отвечает за организацию мероприятий клуба;
2.	SMM – отвечает за ведение медиа каналов. В настоящее время клубу принадлежит группа во Вконтакте (912 участников) и чат в Телеграмме (63 участника);
3.	PR – отвечает за создание и поддержание бренда клуба в глазах общественности, за связь с текущими партнерами и за поиск новых партнеров. В настоящий момент у клуба 17 внешних партнеров, 8 внутренних партнеров и 4 партнера – филиала РЭУ; 
4.	База Знаний – отвечает за ведение 
- Базы Знаний клуба, в которой собрана вся ключевая информация для прокачки навыков в области DS. Она расположена на платформе Notion;
- YouTube канала, содержащего записи мероприятий клуба;
- GitHub профиля, в котором содержатся проекты клуба.
5.	Pet-projects - департамент, отвечающий за развитие навыков и знаний организаторов посредством создания мини-продукта (сайта, бота, программы, ML-модели, исследования и т.д.).
•	Руководители департаментов клуба
У каждого департамента есть руководитель. Он осуществляет стратегическое планирование и управление работой департамента.
•	Организаторы клуба
На данный момент в клубе 19 организаторов. Каждый организатор состоит хотя бы в одном из департаментов клуба. В обязанности организатора входит выполнение поставленных задач, развитие собственных хард и софт скиллов.
•	Менторы
Сейчас в клубе 6 менторов. В их обязанности входит построение образовательной и карьерной траектории для своих менти, а также мониторинг прогресса менти.!

### Миссия
Развитие и популяризация науки о данных среди студентов: приобретение ими необходимых знаний и релевантного опыта для успешного карьерного развития в DS!

### Задачи
1)	Повышение интереса к науке о данных
2)	Концентрация актуальных обучающих материалов и курсов по науке о данных
3)	Создание комьюнити людей, интересующихся наукой о данных для совместного развития в данной сфере
4)	Проведение мероприятий посвященных науке о данных

## Концептуальная модель
Требуется создать базу данных со следующими сущностями: 
1.	Club_members (участники клуба),
2.	Heads (руководители), 
3.	Mentors (менторы), 
4.	Departments (департаменты),
5.	PR (PR-департамент), 
6.	SMM (SMM-департамент), 
7.	Rubrics (рубрики),
8.	Knowledge_base (база знаний),
9.	Events (мероприятия), 
10.	Projects (департамент pet-projects).
Между сущностями необходимо провести следующие связи:
1.	mentors – club_members [1:М] обязательная, не идентифицирующая
У одного ментора может быть несколько менти, причем наличие менти является обязательным условием существования роли ментора. У одного участника может быть только один ментор. Первичный ключ участника не мигрирует в первичный ключ ментора, так что связь не идентифицирующая.
2.	heads – club_members [1:М] обязательная, идентифицирующая
В клубе может быть только один хэд в определенный момент времени. Первичный ключ member_id мигрирует , так что связь идентифицирующая.
3.	departments – SMM [1:M] обязательная, не идентифицирующая
В СММ департаменте может существовать несколько медиа каналов. Первичный ключ не мигрирует, поэтому связь не идентифицирующая.
4.	SMM - rubrics [1:M] обязательная, не идентифицирующая
Для ведения каждого медиа канала используются несколько рубрик. Первичный ключ не мигрирует, поэтому связь не идентифицирующая.
5.	departments – PR [1:M] обязательная, не идентифицирующая
В PR департаменте происходит взаимосвязь с несколькими партнерами. Первичный ключ не мигрирует, поэтому связь не идентифицирующая.
6.	departments – SMM [1:M] обязательная, не идентифицирующая
В СММ департаменте может существовать несколько медиа каналов. Первичный ключ не мигрирует, поэтому связь не идентифицирующая.
7.	departments – Knowledge_base [1:M] обязательная, не идентифицирующая
В департаменте Базы Знаний может существовать несколько инфо продуктов. Первичный ключ не мигрирует, поэтому связь не идентифицирующая.
8.	departments – Events [1:M] обязательная, не идентифицирующая
В департаменте Events организуют множество мероприятий. Первичный ключ не мигрирует, поэтому связь не идентифицирующая.
9.	Club_members – departments [M:M] обязательная, в дальнейшем распадается. 
Организатор клуба может выполнять задачи в разных департаментах. В департаменте над задачами могут работать несколько участников клуба. Так, связь двух сущностей создает новую сущность department_members, первичный ключ которой составляют мигранты-первичные ключи club_members и departments, связь идентифицирующая. 

Теперь перейдем к определению атрибутов сущностей, доменов атрибутов,
уникальных идентификаторов сущностей (первичных ключей): 

1)	Club_members. Сущность содержит информация об именах, фамилиях, датах рождения участиков клуба. Также в атрибуты входят id ментора, дата вступления в клуб, является ли сам участник ментором, id департамента. Первичный ключ – id (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169881595-3191fddc-40aa-401e-a47b-8138ea62d8fc.png">  
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169881615-6d346f47-fb99-4fdb-a450-c36eb14b81ee.png"> 
</p>

2)	Mentors. Сущность содержит информацию об имени ментора и его id. Первичный ключ – id (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169883399-5868eec2-c164-43fb-9fd5-d5cc97909d63.png">  
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169883459-01c2f97f-b966-4fe7-83f0-f64e73543fe5.png">
</p>

3) Heads. Содержит информацию о дате вступления хэда в должность и о его заместителе. Первичный ключ – member_id (мигрировал из club_members).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169883699-7034fbd8-dc47-485f-bcea-152dc6f8c87a.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169883802-4bcfe224-b76a-42e2-8ea4-27aa82d2df7b.png">
</p>

4) Departments. Сущность содержит информацию о ФИО, дате рождения, стаже, зарплате сотрудника. Внешний ключ от сущности profession. Первичный ключ – id (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169884020-9dd8e29e-3a06-4071-b752-bb95a8b07e78.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169884044-0b600612-4927-42d5-bf4e-a8c808348d94.png">
</p>

5) SMM. Сущность содержит информацию о названии, уровне скидки, телефоне для связи компании. Внешний ключ от сущности direction. Первичный ключ – id company (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169884350-bb7bedb5-3f49-42fa-ba09-9a6401a60530.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169884370-c6773f38-6888-4b89-8bbb-0f0803d542cf.png">
</p>

6)	PR. Содержит информацию о стоимости заказа. Внешний ключ от сущности customer. Первичный ключ – id order (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169885818-020be4a8-e79a-4170-a9b0-511e65abe9f7.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169885837-fde20fc3-5107-4495-83d0-5d74a615f627.png">
</p>

7)	Knowledge_base. Содержит информацию о названии изделия. Внешние ключи от сущностей. type_of_product (тип изделия), size_of_product (размер изделия), design_of_product (дизайн изделия). Первичный ключ – id product (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169885944-ce0f48f8-9978-4c42-ba48-57d4aeefc371.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169885968-f300f0fa-e670-497c-b46b-b3ef37a305f7.png">
</p>

8)	Events. Содержит информацию о названии дизайна. Первичный ключ – id design (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169886194-8f999056-877a-4755-9810-1ce243bda87f.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169886224-21d344ef-ff8b-4c33-b135-f7375b7b47d3.png">
</p>

9)	Projects. Содержит информацию о возможных размерах изделий. Первичный ключ – size id (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169886358-6d9197cf-971b-4f3d-9b4a-2c69a2a1da3d.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169886384-97a8fe25-3fb9-43b7-aa15-56d0f95a1d0d.png">
</p>

10)	Rubrics. Содержит информацию о типах продукции. Первичный ключ – type id (искусственный).
<p float="left">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169886519-1434d9ff-edb9-4125-a18a-e02831389ba1.png">
  <img width="200" alt="image" src="https://user-images.githubusercontent.com/76436391/169886542-78136b22-831d-4784-9f6b-5447cb7e1bb4.png">
</p>

| <img width="650" alt="image" src="https://user-images.githubusercontent.com/76436391/169891799-212a17a1-77ff-42db-b591-0283641ba753.png"> |
|:--:| 
| *Концептуальная ER-модель(диаграмма) предметной области* |


| <img width="650" alt="image" src="https://user-images.githubusercontent.com/76436391/169892512-1e4bbe78-fcce-46fb-8141-425f2b96e264.png"> | 
|:--:| 
| *Концептуальная ER-модель предметной области(engineer)* |

## Docker | Dbeaver

Скачиваем Docker: <a href="[https://www.google.com/](https://www.docker.com/products/docker-desktop/)" target="_blank">Ссылка на скачивание</a>

Участники проекта:
* Нина Попова
* Виктор Костырин
* София Николенко
* Владимир Агишев

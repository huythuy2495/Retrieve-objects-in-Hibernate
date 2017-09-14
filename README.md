# Retrieve-objects-in-Hibernate
Criteria cr = session.createCriteria(Employee.class);

// Lấy các record có salary lớn hơn 2000
cr.add(Restrictions.gt("salary", 2000));

// Lấy các record có salary nhỏ hơn 2000
cr.add(Restrictions.lt("salary", 2000));

// Lấy các record có fistName bắt đầu là zara
cr.add(Restrictions.like("firstName", "zara%"));

// Dạng không phân biệt chữ hoa và chữ thường cho điều kiện trên.
cr.add(Restrictions.ilike("firstName", "zara%"));

// Lấy các record có salary trong khoảng 1000 và 2000
cr.add(Restrictions.between("salary", 1000, 2000));

// Check thuộc tính đã cho là null
cr.add(Restrictions.isNull("salary"));

// Check thuộc tính đã cho là khác null
cr.add(Restrictions.isNotNull("salary"));

// Check thuộc tính đã cho là empty
cr.add(Restrictions.isEmpty("salary"));

// Check thuộc tính đã cho là khác empty
cr.add(Restrictions.isNotEmpty("salary"));





Criteria cr = session.createCriteria(Employee.class);

Criterion salary = Restrictions.gt("salary", 2000);
Criterion name = Restrictions.ilike("firstNname","zara%");

// Lấy các record phù hợp với điều kiện OR
LogicalExpression orExp = Restrictions.or(salary, name);
cr.add(orExp);

// Lấy các record phù hợp với điều kiện AND
LogicalExpression andExp = Restrictions.and(salary, name);
cr.add(andExp);

List results = cr.list();




Criteria cr = session.createCriteria(Employee.class);

// Lấy các record có salary lớn hơn 2000
cr.add(Restrictions.gt("salary", 2000));

// Sắp xếp các record theo thứ tự giảm dần
cr.addOrder(Order.desc("salary"));

// Sắp xếp các record theo thứ tự tăng dần
cr.addOrder(Order.asc("salary"));

List results = cr.list();




Criteria cr = session.createCriteria(Employee.class);

// Lấy tổng số hàng.
cr.setProjection(Projections.rowCount());

// Lấy giá trị trung bình của một thuộc tính.
cr.setProjection(Projections.avg("salary"));

// Để có số lần xuất hiện duy nhât của một thuộc tính.
cr.setProjection(Projections.countDistinct("firstName"));

// Lấy giá trị maximum của một thuộc tính.
cr.setProjection(Projections.max("salary"));

// Lấy giá trị minimum của một thuộc tính.
cr.setProjection(Projections.min("salary"));

// Lấy tổng các giá trị của một thuộc tính
cr.setProjection(Projections.sum("salary"));

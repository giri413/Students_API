from flask import Flask, make_response, request, jsonify
from flask_restful import Api
from database.db import initialize_db
from resources.routes import initialize_route

app= Flask(__name__)
api = Api(app)

DB_ATLAS_URI = "mongodb+srv://cst_user:mcit123@cluster0.vo3fn.mongodb.net/mcit?retryWrites=true&w=majority"

app.config["MONGODB_HOST"] = DB_ATLAS_URI

initialize_db(app)
initialize_route(api)

class Students(db.document):
	id = db.IntField()
  	name = db. StringField()
	course = db.StringField()
	program = db.StringField()
	batch = db.StringField()
  	college = db.StringField()
  
	def to_json(self):
		return {
			"id" : self.id,
			"name": self.name,
			"course": self.course,
			"program" : self.program,
			"batch": self.batch,
			"college": self.college
		}


@app.route('/api/db_populate', methods=['POST'])
def db_populate():
	student1 = Student(id=1, name = "giri", course = "Mongo", program = "web application", batch = "Fall 2020", college = "MCIT")
	student2 = Student(id=2, name = "ariel", course = "Rest API", program = "web application", batch = "Fall 2020", college = "MCIT")
	pass
	student1.save()
	student2.save()
	return make_response("",201)

@app.route('/api/students', methods=['GET', 'POST'])
def api_students():
	if request.method = "GET":
		students = []
		for student in Student.objects:
			students.append(student)
		return make_response(jsonify(students), 200)
	elif request.method = "POST":
		content = request.json
		student = student (id=content['id'], name=content['name], course=content['course'], program=content['programe'], batch=content['batch'], college=content['college'])
		student.save()
		retutn make_response("", 201)

@app.route('/api/students/<id>', methods=['GET', 'PUT',  'DELETE'])
def api_each_student(id):
	if request.method = "GET"
		student_obj = student.objects(id=id).first()
		if student_obj:
			return make_response(jsonify(student_obj.to_json()), 200)
		else:
			return make_response("", 404)
	elif request.method = "PUT"
		content = request.json
		student_obj = student.objects(id=id).first()
		student_obj.update(name=content['name'], course=content['course'], program=content['programe'], batch=content['batch'], college=content['college')
		return make_response("", 204)
	elif request.method = "DELETE"
		student_obj = student.objects(id=id).first()
		student_obj.delete()
		return make_response("")

if _name_ = '_main_':
app.run()

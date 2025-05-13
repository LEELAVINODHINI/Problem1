 from flask import Flask, render_template, request
  app = Flask(__name__)
  PARTS = {
    'leg': 250,
    'wing': 250,
    'flesh': 1000
  }
  @app.route('/', methods=['GET', 'POST'])
  def chicken_inventory():
    result = {}
      if request.method == 'POST':
        try:
            legs = int(request.form['legs'])
            wings = int(request.form['wings'])
            flesh = int(request.form['flesh'])
            order_weight = (legs * PARTS['leg']) + (wings * PARTS['wing']) + (flesh * PARTS['flesh'])
            needed_legs = -(-legs // 2)
            needed_wings = -(-wings // 2)
            needed_flesh = flesh
            chickens_needed = max(needed_legs, needed_wings, needed_flesh)
            total_legs = chickens_needed * 2
            total_wings = chickens_needed * 2
            total_flesh = chickens_needed * 1
            remaining_legs = total_legs - legs
            remaining_wings = total_wings - wings
            remaining_flesh = total_flesh - flesh
            remaining_weight = (remaining_legs * PARTS['leg']) + (remaining_wings * PARTS['wing']) + (remaining_flesh * PARTS['flesh'])
            result = {
                'order_weight': order_weight / 1000,  # in kg
                'chickens_needed': chickens_needed,
                'remaining_legs': remaining_legs,
                'remaining_wings': remaining_wings,
                'remaining_flesh': remaining_flesh,
                'remaining_weight': remaining_weight / 1000  # in kg
            }
        except ValueError:
            result['error'] = "Invalid input. Please enter valid numbers."
      return render_template('index.html', result=result)
  if __name__ == '__main__':
      app.run(debug=True)
  

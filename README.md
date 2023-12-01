from tkinter import *
from tkinter import messagebox  # Import messagebox for showing alerts
from PIL import Image, ImageTk

# Create a main window
mainwindow = Tk()

# Creating frame
frame1 = LabelFrame(mainwindow, text="picture")
frame1.grid(rowspan=10, columnspan=10)

# create frame 2
frame2 = LabelFrame(mainwindow, text="Frame2")
frame2.grid(rowspan=10, columnspan=10)


# Create a new window for Pick-up Schedule
def pick_up_schedule_window():

  def submit_pick_up_schedule():
    selected_day = day_var.get()
    selected_time = time_var.get()
    messagebox.showinfo(
        "Schedule Submitted",
        f"Pick-up scheduled for {selected_day} at {selected_time}.")

  newWindow = Toplevel()
  newWindow.title("Pick-up Schedule")

  # add label for Pick-up Day
  day_label = Label(newWindow, text="Pick-up Day")
  day_label.grid(row=2, column=0, pady=10)

  # add entry box for Pick-up Day
  day_var = StringVar(newWindow)
  days = [
      "Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday",
      "Sunday"
  ]
  day_dropdown = OptionMenu(newWindow, day_var, *days)
  day_dropdown.grid(row=2, column=5)

  # add label for Pick-up Time
  time_label = Label(newWindow, text="Pick-up Time")
  time_label.grid(row=3, column=0, pady=10)

  # add entry box for Pick-up Time
  time_var = StringVar(newWindow)
  times = ["8:00 AM", "10:00 AM", "12:00 PM", "2:00 PM", "4:00 PM"]
  time_dropdown = OptionMenu(newWindow, time_var, *times)
  time_dropdown.grid(row=3, column=5)

  # add button to submit pick-up schedule
  submit_button = Button(newWindow,
                         text="Submit",
                         command=submit_pick_up_schedule)
  submit_button.grid(row=4, column=0, columnspan=2, pady=10)


# Create a new window for Create Record
def create_record_window():

  def submit_create_record():
    first_name = enterfname.get()
    last_name = enterlname.get()
    age_val = enterage.get()
    address1_val = enteraddress1.get()
    address2_val = enteraddress2.get()
    zip_code_val = enterzip_code.get()
    phone_number_val = enterphone_number.get()
    email_address_val = enteremail_address.get()

    messagebox.showinfo(
        "Record Created",
        f"Record created for {first_name} {last_name} with Age: {age_val}, Address: {address1_val}, {address2_val}, Zip Code: {zip_code_val}, Phone Number: {phone_number_val}, Email: {email_address_val}"
    )

  newWindow = Toplevel()
  newWindow.title("Create Record")

  # add label for firstname to frame1
  fname = Label(newWindow, text='Firstname')
  fname.grid(row=2, column=0, pady=10)

  # add entry box to frame 1
  enterfname = Entry(newWindow, width=20)
  enterfname.grid(row=2, column=5)

  # add label for lastname to frame 1
  lname = Label(newWindow, text="Last name")
  lname.grid(row=3, column=0, pady=10)

  # add entry box
  enterlname = Entry(newWindow, width=20)
  enterlname.grid(row=3, column=5)

  # add label for age to frame 1
  age = Label(newWindow, text="Age")
  age.grid(row=5, column=0)

  # add entry box
  enterage = Entry(newWindow, width=10)
  enterage.grid(row=5, column=5)

  # add label for Address1 to frame 1
  address1 = Label(newWindow, text="Address1")
  address1.grid(row=6, column=0, pady=10)

  # add entry box
  enteraddress1 = Entry(newWindow, width=20)
  enteraddress1.grid(row=6, column=5)

  # add label for Address2 to frame 1
  address2 = Label(newWindow, text="Address2")
  address2.grid(row=7, column=0, pady=10)

  # add entry box
  enteraddress2 = Entry(newWindow, width=20)
  enteraddress2.grid(row=7, column=5)

  # add label for Zip Code to frame 1
  zip_code = Label(newWindow, text="Zip Code")
  zip_code.grid(row=8, column=0, pady=10)

  # add entry box
  enterzip_code = Entry(newWindow, width=20)
  enterzip_code.grid(row=8, column=5)

  # add label for Phone_Number to frame 1
  Phone_Number = Label(newWindow, text="Phone Number")
  Phone_Number.grid(row=9, column=0, pady=10)

  # add entry box
  enterphone_number = Entry(newWindow, width=20)
  enterphone_number.grid(row=9, column=5)

  # add label for Email_Address to frame 1
  email_address = Label(newWindow, text="Email Address")
  email_address.grid(row=10, column=0, pady=10)

  # add entry box
  enteremail_address = Entry(newWindow, width=20)
  enteremail_address.grid(row=10, column=5)

  # add button to submit create record
  submit_button = Button(newWindow,
                         text="Submit",
                         command=submit_create_record)
  submit_button.grid(row=11, column=0, columnspan=2, pady=10)


# Create a new window for Trash Weight
def trash_weight_window():
  newWindow = Toplevel()
  newWindow.title("Trash Weight")

  # add label for Trash Weight
  trash_weight_label = Label(newWindow, text="Trash Weight (lbs)")
  trash_weight_label.grid(row=2, column=0, pady=10)

  # add entry box for Trash Weight
  enter_trash_weight = Entry(newWindow, width=20)
  enter_trash_weight.grid(row=2, column=5)

  # add button to calculate payment
  calculate_payment_button = Button(
      newWindow,
      text="Calculate Payment",
      command=lambda: calculate_payment(enter_trash_weight, payment_label))
  calculate_payment_button.grid(row=3, column=0, columnspan=2, pady=10)

  # label to display the calculated payment
  payment_label = Label(newWindow, text="Payment: $0.00")
  payment_label.grid(row=4, column=0, columnspan=2, pady=10)


# Function to calculate payment based on trash weight
def calculate_payment(enter_trash_weight, payment_label):
  try:
    trash_weight = float(enter_trash_weight.get())
    # You can adjust the payment calculation logic here
    payment = trash_weight * 0.5  # Example: $0.50 per pound
    payment_label.config(text=f"Payment: ${payment:.2f}")
  except ValueError:
    payment_label.config(text="Invalid input. Please enter a valid number.")


# Create a new window for Payment
def payment_window():
  newWindow = Toplevel()
  newWindow.title("Payment")

  # add label for Payment Amount
  payment_label = Label(newWindow, text="Enter Payment Amount")
  payment_label.grid(row=2, column=0, pady=10)

  # add entry box for Payment Amount
  enter_payment_amount = Entry(newWindow, width=20)
  enter_payment_amount.grid(row=2, column=5)

  # add button to submit payment
  submit_payment_button = Button(
      newWindow,
      text="Submit Payment",
      command=lambda: submit_payment(enter_payment_amount))
  submit_payment_button.grid(row=3, column=0, columnspan=2, pady=10)


# Function to submit payment
def submit_payment(enter_payment_amount):
  try:
    payment_amount = float(enter_payment_amount.get())
    # You can add logic to handle the payment submission (e.g., connect to payment gateway, update payment status)
    messagebox.showinfo(
        "Payment Successful",
        f"Payment of ${payment_amount:.2f} submitted successfully!")
  except ValueError:
    messagebox.showerror("Invalid Input",
                         "Please enter a valid payment amount.")


# create buttons 1
createrecord = Button(frame2,
                      text="Create Record",
                      command=create_record_window)
createrecord.grid(row=0, column=1)

# create buttons 2
pick_up_schedule = Button(frame2,
                          text="Pick-up Schedule",
                          command=pick_up_schedule_window)
pick_up_schedule.grid(row=1, column=1)

# create buttons 3
trash_weight = Button(frame2, text="Trash Weight", command=trash_weight_window)
trash_weight.grid(row=2, column=1)

# create buttons 4
pay = Button(frame2, text="Pay", command=payment_window)
pay.grid(row=3, column=1)

mainwindow.mainloop()  # All codes need to be between mainwindow & main loop

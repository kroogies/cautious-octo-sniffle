  def getdata():
      get_input = id_entry.get()

      if get_input != '':
          con = sqlite3.connect('contacts1.db')
          c = con.cursor()
          c.execute("SELECT * FROM contacts WHERE rowid = :id_entry", get_input)
          data = c.fetchall()


          def show_fields():
              searchbtn.destroy()
              id_entry.destroy()
              id_text.destroy()
              searched_contact.destroy()

              # first name entry and label
              fnamevar = StringVar()
              fname_entry = Entry(window2, font=('@Yu Gothic Light', 18), relief=SOLID, borderwidth=3,
                                  textvariable=fnamevar)
              fname_entry.place(x=30, y=80,
                                width=300, height=30)
              fname_text = Label(window2, text='F I R S T   N A M E', font=('@Yu Gothic Light', 15),
                                 fg='#ffffff',
                                 bg='#0f0f0f')
              fname_text.place(x=30, y=50)

              # last name entry and label
              lnamevar = StringVar()
              lname_entry = Entry(window2, font=('@Yu Gothic Light', 18), relief=SOLID, borderwidth=3,
                                  textvariable=lnamevar)
              lname_entry.place(x=30, y=150,
                                width=300, height=30)
              lname_text = Label(window2, text='L A S T   N A M E', font=('@Yu Gothic Light', 15), fg='#ffffff',
                                 bg='#0f0f0f')
              lname_text.place(x=30, y=120)

              # email entry and label
              emailvar = StringVar()
              email = Entry(window2, font=('@Yu Gothic Light', 18), relief=SOLID, borderwidth=3,
                            textvariable=emailvar)
              email.place(x=30, y=230,
                          width=300, height=30)
              e_label = Label(window2, text='E M A I L   A D D R E S S', font=('@Yu Gothic Light', 15),
                              fg='#ffffff',
                              bg='#0f0f0f')
              e_label.place(x=30, y=200)

              # phone number entry and label
              nmbrvar = StringVar()
              nmbr = Entry(window2, font=('@Yu Gothic Light', 18), relief=SOLID, borderwidth=3,
                           textvariable=nmbrvar)
              nmbr.place(x=30, y=310,
                         width=300, height=30)
              nmbr_label = Label(window2, text='P H O N E   N U M B E R', font=('@Yu Gothic Light', 15),
                                 fg='#ffffff',
                                 bg='#0f0f0f')
              nmbr_label.place(x=30, y=280)

              for i in data:
                  fnamevar.set(i[0])
                  lnamevar.set(i[1])
                  nmbrvar.set(str(i[2]))
                  emailvar.set(i[3])

              # edit contact btn function
              # this is the part where I'm having problems with: eddb
              def eddb():
                  fields = [fname_entry.get(), lname_entry.get(), nmbr.get(), email.get(), id_entry.get()]

                  try:
                      fields[2] == str(int(fields[2]))
                  except ValueError:
                      messagebox.showerror('Error', 'Numbers only please')

                  if fields[2] == str(int(fields[2])):
                      con = sqlite3.connect('contacts1.db')
                      cursor = con.cursor()
                      cursor.execute("UPDATE contacts SET Fname = :fname_entry, Lname = :lname_entry, PNumber = :nmbr, Email = :email WHERE rowid = contact_id", fields)

                      con.commit()
                      con.close()

                      fname_entry.delete(0, END)
                      lname_entry.delete(0, END)
                      nmbr.delete(0, END)
                      email.delete(0, END)

              # edit contact btn
              editbtn = Button(window2, text='U P D A T E', font=('@Yu Gothic Light', 16), fg='#000000', bg='#ffffff',
                              relief=SOLID, borderwidth=3, activeforeground='#000000', activebackground='#bdbebf',
                              command=eddb)  # added command, might bug out tho
              editbtn.place(x=115, y=370,
                           width=120, height=45)

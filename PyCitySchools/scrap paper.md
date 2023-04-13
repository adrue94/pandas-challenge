school_types
per_school_counts
per_school_capita
per_school_math
school_passing_math
school_passing_reading
per_school_passing_math
per_school_passing_reading
passing_math_and_reading
overall_passing_rate

df = pd.DataFrame([('bird', 389.0),
                   ('bird', 24.0),
                   ('mammal', 80.5),
                   ('mammal', np.nan)],
                  index=['falcon', 'parrot', 'lion', 'monkey'],
                  columns=('class', 'max_speed'))
df
         class  max_speed
falcon    bird      389.0
parrot    bird       24.0
lion    mammal       80.5
monkey  mammal        NaN

-----------------------------------------------------------------

per_school_summary_one = pd.DataFrame({
        'School Type':                  (school_types.values),
        'Total Students':               (per_school_counts.values),
}, index=[school_data_complete['school_name'].unique()])
per_school_summary_one

-----------------------------------------------------------------

per_school_summary_two = pd.DataFrame({
    'Total School Budget':          (per_school_budget.values),
    'Per Student Budget':           (per_school_capita.values),
    'Per Student Budget':           (per_school_capita.values),
    'Average Math Score':           (per_school_math.values), 
    'Average Reading Score':        (per_school_reading.values),
    '% Passing Math':               (per_school_passing_math.values),
    '% Passing Reading':            (per_school_passing_reading.values),
    '% Overall Passing':            (overall_passing_rate.values),
},index=[school_name])

# Formatting
per_school_summary_two["Total School Budget"] = per_school_summary_two["Total School Budget"].map("${:,.2f}".format)
per_school_summary_two["Per Student Budget"] = per_school_summary_two["Per Student Budget"].map("${:,.2f}".format)


# Display the DataFrame
per_school_summary_two

-----------------------------------------------------------------

per_school_summary = per_school_summary_one.join(per_school_summary_two)
per_school_summary.sort_index()

-----------------------------------------------------------------
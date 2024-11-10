def find_strongest_trainees():
    # Read the strength data
    strengths = []
    for i in range(12):
        try:
            strength = int(input())
            if strength < 1 or strength > 200:
                print("INVALID INPUT")
                return
            strengths.append(strength)
        except ValueError:
            print("INVALID INPUT")
            return
    
    # Organize the strengths into 4 trainees, each having 3 rounds of strength values
    trainees_strength = []
    for i in range(4):
        trainees_strength.append(strengths[i*3:i*3+3])
    
    # Calculate average strength for each trainee
    averages = []
    for i in range(4):
        avg_strength = round(sum(trainees_strength[i]) / 3)
        averages.append(avg_strength)
    
    # Find the maximum average strength
    max_avg = max(averages)
    
    # If the maximum average strength is less than 100, output that all are unfit
    if max_avg < 100:
        print("All trainees are unfit.")
        return
    
    # Output the trainee(s) with the highest average strength
    for i in range(4):
        if averages[i] == max_avg:
            print(f"Trainee Number : {i + 1}")

# Call the function to process the input and produce the output
find_strongest_trainees()

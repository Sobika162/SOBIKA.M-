smart_traffic_analyzer/main.py

from traffic_simulation import TrafficSimulator from traffic_light_controller import TrafficLightController

def main(): controller = TrafficLightController() simulator = TrafficSimulator(controller)

print("Starting Smart Traffic Flow Analyzer...")
simulator.run_simulation()

if name == "main": main()

smart_traffic_analyzer/traffic_simulation.py

import time import random

class TrafficSimulator: def init(self, controller): self.controller = controller self.lanes = ["North", "South", "East", "West"]

def run_simulation(self, cycles=5):
    for _ in range(cycles):
        traffic_data = {
            lane: random.randint(0, 10) for lane in self.lanes
        }
        print(f"\nTraffic data: {traffic_data}")
        next_green = self.controller.decide_next_light(traffic_data)
        self.display_signal(next_green)
        time.sleep(2)

def display_signal(self, green_lane):
    print(f"\n--- GREEN LIGHT: {green_lane.upper()} ---")
    for lane in self.lanes:
        if lane != green_lane:
            print(f"{lane}: RED")
    print(f"{green_lane}: GREEN")

smart_traffic_analyzer/traffic_light_controller.py

class TrafficLightController: def decide_next_light(self, traffic_data): # Choose the lane with highest vehicle count return max(traffic_data, key=traffic_data.get)

smart_traffic_analyzer/README.md

Smart Traffic Flow Analyzer 🚦

A Python-based simulation of a smart traffic light system that dynamically adjusts based on simulated traffic density.

Features

Randomized traffic generation for 4-way intersection

Smart traffic light control based on density

CLI-based simulation output

Easy to extend with GUI or ML models


Getting Started

git clone https://github.com/yourusername/smart-traffic-analyzer.git
cd smart-traffic-analyzer
python main.py

Future Enhancements

GUI using Tkinter or Pygame

Real-time video integration with OpenCV

Machine Learning model for prediction



---

Feel free to fork and improve!

smart_traffic_analyzer/requirements.txt

No external libraries required (uses standard Python libraries)

Optional for future use:

opencv-python

numpy

pygame

scikit-learn

